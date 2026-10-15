# Inspector: Browse agent trajectories

!!! abstract "Overview"

    * The `inspector` is a tool that allows you to browse `.traj.json` files that show the history of a Leanimum-agent run.
    * Quickly start it with `leani-e i` or `leani-extra inspector`.
    * See [output files](output_files.md) for the trajectory file format.
    * Alternative: [jless](https://jless.io/) is a great command-line JSON viewer for browsing trajectories.


## Usage

```bash
# Find all .traj.json files recursively from current directory
leani-extra inspector
# or shorter
leani-e i
# Open the inspector for a specific file
leani-e i <path_to_traj.json>
# Search for trajectory files in a specific directory
leani-e i <path_to_directory>
```

## Key bindings

- `q`: Quit the inspector
- `h`/`LEFT`: Previous step
- `l`/`RIGHT`: Next step
- `j`/`DOWN`: Scroll down
- `k`/`UP`: Scroll up
- `H`: Previous trajectory
- `L`: Next trajectory
- `e`: Open current step in [jless](https://jless.io/)

### FAQ

> How can I select/copy text on the screen?

Hold down the `Alt`/`Option` key and use the mouse to select the text.

## Implementation

The inspector is implemented with [textual](https://textual.textualize.io/).

??? note "Implementation"

    - [Read on GitHub](https://github.com/cmu-l3/Leanimum-agent/blob/main/src/leanimum/run/utilities/inspector.py)

    ```python linenums="1"
    --8<-- "src/leanimum/run/utilities/inspector.py"
    ```

{% include-markdown "../_footer.md" %}