# Quick start

!!! tip "Installation Options"

    === "pip"

        Use pip to install `leani` in your current environment:

        ```bash
        pip install "git+https://github.com/cmu-l3/Leanimum-agent.git"
        ```

        And try our command line interface

        ```bash
        leani  # CLI
        leani-extra  # extra utilities
        ```

    === "uv (isolated)"

        Use `uv`/`uvx` ([installation](https://docs.astral.sh/uv/getting-started/installation/)) to directly run the `leani` CLI.
        Use this if you're only interested in the CLI but don't need python bindings (`leani` will be installed in an anonymous virtual environment).

        Quickly install + run:

        ```bash
        uvx --from "git+https://github.com/cmu-l3/Leanimum-agent.git" leani  # CLI
        uvx --from "git+https://github.com/cmu-l3/Leanimum-agent.git" leani-extra  # extra utilities
        ```

        Permanently install

        ```bash
        uv tool install "git+https://github.com/cmu-l3/Leanimum-agent.git"
        # then
        leani  # CLI
        leani-extra  # extra utilities
        ```

    === "pipx (isolated)"

        Use pipx ([installation](https://pipx.pypa.io/stable/how-to/install-pipx.html)) to directly run the `leani` CLI.
        Use this if you're only interested in the CLI but don't need python bindings (`leani` will be installed in an anonymous virtual environment).

        Quick install + run:

        ```bash
        # CLI
        pipx run --spec "git+https://github.com/cmu-l3/Leanimum-agent.git" leani
        # Extra utilities
        pipx run --spec "git+https://github.com/cmu-l3/Leanimum-agent.git" leani-extra
        ```

        or for a persistent installation (recommended):

        ```bash
        pipx install "git+https://github.com/cmu-l3/Leanimum-agent.git"
        # then
        leani  # CLI
        leani-extra  # extra utilities
        ```

        If the invocation doesn't immediately work, you might need to run `pipx ensurepath`.

    === "From source/dev"

        For development or if you want to customize the agent:

        ```bash
        git clone https://github.com/cmu-l3/Leanimum-agent.git
        cd Leanimum-agent
        pip install -e .
        ```

        Then run:

        ```bash
        leani  # CLI
        leani-extra  # extra utilities
        ```

        Or pick a [run script](https://github.com/cmu-l3/Leanimum-agent/tree/main/src/leanimum/run):

        ```bash
        python src/leanimum/run/hello_world.py
        ```

        If you are planning to contribute, please also install the dev dependencies
        and `pre-commit` hooks:

        ```bash
        pip install -e '.[dev]'
        pip install pre-commit && pre-commit install
        ```

        To check your installation, you can run `pytest -n auto` in the root folder.
        This should run all tests in parallel (should take ~3min to run).

        Note that there are still some extra dependencies that are not installed by default
        (basically anything that is in an `.../extra/...` folder).
        If you truly want to get the maximal package, you can run `pip install -e '.[full]'`

!!! note "Changelog"

    Please see the [github release notes](https://github.com/cmu-l3/Leanimum-agent/releases) for recent changes.

!!! example "Example Prompts"

    Try Leanimum-agent with these example prompts:

    - Implement a Sudoku solver in python in the `sudoku` folder. Make sure the codebase is modular and well tested with pytest.
    - Please run pytest on the current project, discover failing unittests and help me fix them. Always make sure to test the final solution.
    - Help me document & type my codebase by adding short docstrings and type hints.

## Models

!!! note "Models should be set up the first time you run `leani`"

    * If you missed the setup wizard, just run `leani-extra config setup`
    * For more information, please check the [model setup quickstart](models/quickstart.md).
    * If you want to use local models, please check this [guide](models/local_models.md).

    Tip: Please always include the provider in the model name, e.g., `anthropic/claude-...`.
