# ConTree

!!! note "ConTree Environment class"

    - [Read on GitHub](https://github.com/cmu-l3/Leanimum-agent/blob/main/src/leanimum/environments/extra/contree.py)
    - Requires [ConTree](https://contree.dev) token

    ??? note "Full source code"

        ```python
        --8<-- "src/leanimum/environments/extra/contree.py"
        ```

::: leanimum.environments.extra.contree

This environment executes commands in [ConTree](https://contree.dev) sandboxes using [ConTree SDK](https://github.com/nebius/contree-sdk)

## Setup

1. Install the dependencies:
   ```bash
   pip install "leanimum-agent[contree] @ git+https://github.com/cmu-l3/Leanimum-agent.git"
   ```

2. Set up ConTree token and base_url:
   ```bash
   export CONTREE_TOKEN="your-contree-token"
   export CONTREE_BASE_URL="your-given-base-url-for-contree"
   ```

## Usage

Use this backend from the generic CLI with a suitable image:

```bash
leani -c mini.yaml --environment-class contree \
  -c environment.image=YOUR_IMAGE -c contree-config.yaml -t "YOUR_TASK"
```

Set `environment.contree_config` in `contree-config.yaml`. Provide the remaining backend settings through YAML; see the class configuration
in the source above.

{% include-markdown "../../_footer.md" %}
