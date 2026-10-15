# SWE-ReX Modal

!!! note "SWE-ReX Modal Environment class"

    - [Read on GitHub](https://github.com/cmu-l3/Leanimum-agent/blob/main/src/leanimum/environments/extra/swerex_modal.py)
    - Requires [Modal](https://modal.com) account and authentication

This environment executes commands in [Modal](https://modal.com) sandboxes using [SWE-ReX](https://github.com/swe-agent/swe-rex).

## Setup

1. Install the full dependencies:
   ```bash
   pip install "leanimum-agent[full] @ git+https://github.com/cmu-l3/Leanimum-agent.git"
   ```

2. Set up Modal authentication:
   ```bash
   modal setup
   ```

## Usage

Use this backend from the generic CLI with a suitable image:

```bash
leani -c mini.yaml --environment-class swerex_modal \
  -c environment.image=YOUR_IMAGE -t "YOUR_TASK"
```

Provide the remaining backend settings through YAML; see the class configuration
in the source above.

{% include-markdown "../../_footer.md" %}
