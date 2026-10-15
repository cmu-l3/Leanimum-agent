# Python bindings

!!! abstract "Overview"

    This page shows the most basic example of how to use Leanimum-agent as a Python library.
    For more advanced usage, subclassing, and mix & match of components, see [subclassing and more](../advanced/cookbook.md).

## Hello world

```python
import logging

from leanimum.agents.default import DefaultAgent
from leanimum.config import get_config_from_spec
from leanimum.models import get_model
from leanimum.environments.local import LocalEnvironment

logging.basicConfig(level=logging.DEBUG)
task = "Write and check a hello world program in Lean"
model_name = "anthropic/claude-sonnet-4-5-20250929"
config = get_config_from_spec("mini")

agent = DefaultAgent(
    get_model(input_model_name=model_name, config=config["model"]),
    LocalEnvironment(cwd="/absolute/path/to/lean-project"),
    **config["agent"],
)

# Run the agent
agent.run(task)
```

{% include-markdown "../_footer.md" %}
