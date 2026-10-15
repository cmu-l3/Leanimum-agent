# Global configuration

!!! abstract "Configuring leani"

    * This guide shows how to configure the `leani` agent's global settings (API keys, default model, etc.).
      Basically anything that is set as environment variables or similar.
    * You should already be familiar with the [quickstart guide](../quickstart.md).
    * For more agent specific settings, see the [yaml configuration file guide](yaml_configuration.md).

!!! tip "Setting up models"

    Setting up models is also covered in the [quickstart guide](../quickstart.md).

## Setting global configuration

All global configuration can be either set as environment variables, or in the `.env` file (the exact location is printed when you run `leani`).
Environment variables take precedence over variables set in the `.env` file.

We provide several helper functions to update the global configuration.

For example, to set the default model and API keys, you can run:

```bash
leani-extra config setup
```

or to update specific settings:

```
leani-extra config set KEY VALUE
# e.g.,
leani-extra config set LEANA_MODEL_NAME "anthropic/claude-sonnet-4-5-20250929"
leani-extra config set ANTHROPIC_API_KEY "sk-..."
```

or to unset a key:

```bash
leani-extra config unset KEY
# e.g.,
leani-extra config unset ANTHROPIC_API_KEY
```

You can also edit the `.env` file directly and we provide a helper function for that:

```bash
leani-extra config edit
```

To set environment variables (recommended for temporary experimentation or API keys):

```bash
export KEY="value"
# windows:
setx KEY "value"
```

## Models, keys, costs

!!! tip "See also"

    Read the [quickstart guide](../quickstart.md) first—it already covers most of this.

```bash
# Default model name
# (default: not set)
LEANA_MODEL_NAME="anthropic/claude-sonnet-4-5-20250929"
```

To ignore errors from cost tracking checks (for example for free models), set:

```bash
# CAREFUL: This can lead to unmanaged spending!
LEANA_COST_TRACKING="ignore_errors"
```

To register extra models to litellm (see [local models](../models/local_models.md) for more details), you can either specify the path in the agent file, or set

```bash
LITELLM_MODEL_REGISTRY_PATH="/path/to/your/model/registry.json"
```

Global cost limits:

```bash
# Global limit on number of model calls (0 = no limit)
# (default: 0)
LEANA_GLOBAL_CALL_LIMIT="100"

# Global cost limit in dollars (0 = no limit)
# (default: 0)
LEANA_GLOBAL_COST_LIMIT="10.00"

# Number of retry attempts for model API calls
# (default: 10)
LEANA_MODEL_RETRY_STOP_AFTER_ATTEMPT="10"
```

## Default config files

```bash
# Set a custom directory for agent config files in addition to the builtin ones
# This allows to specify them by names
LEANA_CONFIG_DIR="/path/to/your/own/config/dir"

# Config path for leani run script
# (default: package_dir / "config" / "mini.yaml")
LEANA_MINI_CONFIG_PATH="/path/to/your/own/config"

# Custom style path for trajectory inspector
# (default: package_dir / "config" / "inspector.tcss")
LEANA_INSPECTOR_STYLE_PATH="/path/to/your/inspector/style.tcss"
```

### Settings for environments

```bash
# Path/name to the singularity/apptainer executable
# (default: "singularity")
LEANA_SINGULARITY_EXECUTABLE="singularity"

# Path/name to the docker executable
# (default: "docker")
LEANA_DOCKER_EXECUTABLE="docker"

# Path/name to the bubblewrap executable
# (default: "bwrap")
LEANA_BUBBLEWRAP_EXECUTABLE="bwrap"
```

{% include-markdown "../_footer.md" %}
