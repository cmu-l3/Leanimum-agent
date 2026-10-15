# FAQ

## General

!!! question "Does Leanimum-agent work on my system?"

    Leanimum-agent should work on any system that has a bash shell or uses a container runtime (e.g., docker, singularity, apptainer, etc.) to emulate one.

??? question "What keeps the agent simple?"

    `leani` keeps its execution model simple:

    - Does not have any tools other than bash. The default model uses bash tool calls; text command blocks are also supported.
      This means you don't have to install anything in any environment you're running in. `bash` is all you need.
    - Has a completely linear history — every step of the agent just appends to the messages and that's it.
    - Executes actions with `subprocess.run` — every action is completely independent (as opposed to keeping a stateful shell session running).
      This [avoids so many issues](#why-no-shell-session), trust me.

??? question "What are the limitations of Leanimum-agent?"

    Leanimum-agent can be extended trivially in various ways, the following assumes the default setup.

    - No tools other than bash
    - Actions use bash tool calls by default; text command blocks are also supported
    - By default, actions are executed as `subprocess.run`, i.e., every action is independent of the previous ones.
      (meaning that the agent cannot change directories or export environment variables; however environment variables
      can be set per-action). This [avoids so many issues](#why-no-shell-session), trust me.


??? question "Where is global configuration stored?"

    The global configuration is stored in the `.env` file in the config directory.
    The location is printed when you run `leani --help`.

    The `.env` file is a simple key-value file that is read by the `dotenv` library.


## Models

!!! question "What models do you support?"

    Currently, Leanimum-agent supports all models that are supported by [litellm](https://github.com/BerriAI/litellm)
    or [OpenRouter](https://openrouter.ai/)
    and we're open to extend the `models/` directory with more models should `litellm` not support them.

!!! question "How do I set the API key for a model?"

    The API key can be stored either as an environment variable (note that enviroinment variables are not persistent
    unless you set them in your `~/.bashrc` or similar), or as a permanent key in the config file.

    To temporarily set the API key as an environment variable, you can use the following command:

    ```bash
    export OPENAI_API_KEY=sk-test123
    ```

    To permanently set the API key in the config file, you can use the following command:

    ```bash
    leani-extra config set OPENAI_API_KEY sk-test123
    ```

    Alternatively, you can directly edit the `.env` file in the config directory
    (the location is printed when you run `leani --help`).

!!! question "How can I set the default model?"

    The default model is stored in the config/environment as `LEANA_MODEL_NAME`.
    To permanently change it:

    ```bash
    leani-extra config set LEANA_MODEL_NAME anthropic/claude-sonnet-4-5-20250929
    ```

    Alternatively, you can directly edit the `.env` file in the config directory
    (the location is printed when you run `leani --help`).

## Minutia

??? question "Why is not needing a running shell session such a big deal?"
    <a name="why-no-shell-session"></a>

    Most agents so far kept a running shell session. Every action from the agent was executed in this session.
    However, this is far from trivial:

    1. It's not obvious when a command has terminated. Essentially you're just pasting input into the shell session, and press enter—but when do you stop reading output?
       We've experimented with various heuristics (watching PIDs, watching for the shell to go back to the prompt, etc.) but all of them were flaky.
       The `leani` agent doesn't need any of this!
    2. Particularly bad commands from the LM can kill the shell session. Then what?
    3. Interrupting a command running in a shell session can also mess up the shell itself and can in particular interfere with all the following outputs you want to extract.

    `leani` is different: There is no running shell session. Every action is executed as a subprocess, that means
    every action is independent of the previous ones (it is literally a `subprocess.run`/`os.system`/`docker exec` call).

    This means that the agent cannot even change directories or export environment variables.
    But you don't need this! You can always prefix `cd /path/to/project` or `export FOO=bar` to every action
    (and in fact some LMs like Claude will do that even if you don't ask them to).

{% include-markdown "_footer.md" %}
