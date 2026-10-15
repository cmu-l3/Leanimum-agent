# Leanimum-agent

A minimal bash-only agent for Lean proofs and programs, based on
[mini-swe-agent](https://github.com/SWE-agent/mini-swe-agent).
Use [leani](usage/mini.md) interactively or run the [ReuF2F benchmark](usage/reuf2f.md).

??? note "Why use Leanimum-agent for research?"

    The `leani` agent:

    - **Does not have any tools other than bash**. The default model uses bash tool calls; text command blocks are also supported.
      This means that you can run it with literally any model.
      When running in sandboxed environments you also don't need to take care of installing a single package — all it needs is bash.
    - **Has a completely linear history** — every step of the agent just appends to the messages and that's it.
      So there's no difference between the trajectory and the messages that you pass on to the LM.
      Great for debugging & fine-tuning.
    - **Executes actions with `subprocess.run`** — every action is completely independent (as opposed to keeping a stateful shell session running). This makes it trivial to execute the actions in sandboxes (literally just switch out `subprocess.run` with `docker exec`) and to scale up effortlessly.
      Seriously, this is [a big deal](faq.md#why-no-shell-session), trust me.

??? note "Why use Leanimum-agent as a tool?"

    Some agents are overfitted research artifacts. Others are UI-heavy frontend monsters.

    The `leani` agent wants to be a hackable tool, not a black box.

    - **Simple** enough to understand at a glance
    - **Convenient** enough to use in daily workflows
    - **Flexible** to extend

    - **Does not have any tools other than bash**. The default model uses bash tool calls; text command blocks are also supported.
      Instead of implementing custom tools for every specific thing the agent might want to do, the focus is fully on the LM utilizing the shell to its full potential.
      Want it to do something specific like opening a PR?
      Just tell the LM to figure it out rather than spending time to implement it in the agent.
    - **Executes actions with `subprocess.run`** — every action is completely independent (as opposed to keeping a stateful shell session running).
      This is [a big deal](faq.md#why-no-shell-session) for the stability of the agent, trust me.
    - **Has a completely linear history** — every step of the agent just appends to the messages that are passed to the LM in the next step and that's it.
      This is great for debugging and understanding what the LM is prompted with.

## Continue reading:

<div class="grid cards">
  <a href="quickstart/" class="nav-card-link">
    <div class="nav-card">
      <div class="nav-card-header">
        <span class="material-icons nav-card-icon">launch</span>
        <span class="nav-card-title">Installation & Quick Start</span>
      </div>
      <p class="nav-card-description">Get started with Leanimum-agent</p>
    </div>
  </a>

  <a href="usage/mini/" class="nav-card-link">
    <div class="nav-card">
      <div class="nav-card-header">
        <span class="material-icons nav-card-icon">flash_on</span>
        <span class="nav-card-title">Usage: Simple UI</span>
      </div>
      <p class="nav-card-description">Learn to use the <code>leani</code> command</p>
    </div>
  </a>

  <a href="faq/" class="nav-card-link">
    <div class="nav-card">
      <div class="nav-card-header">
        <span class="material-icons nav-card-icon">help</span>
        <span class="nav-card-title">FAQ</span>
      </div>
      <p class="nav-card-description">Common questions and answers</p>
    </div>
  </a>

  <a href="advanced/yaml_configuration/" class="nav-card-link">
    <div class="nav-card">
      <div class="nav-card-header">
        <span class="material-icons nav-card-icon">settings</span>
        <span class="nav-card-title">Configuration</span>
      </div>
      <p class="nav-card-description">Setup and customize your agent</p>
    </div>
  </a>

  <a href="advanced/cookbook/" class="nav-card-link">
    <div class="nav-card">
      <div class="nav-card-header">
        <span class="material-icons nav-card-icon">fitness_center</span>
        <span class="nav-card-title">Power up</span>
      </div>
      <p class="nav-card-description">Start hacking the agent!</p>
    </div>
  </a>
</div>

{% include-markdown "_footer.md" %}
