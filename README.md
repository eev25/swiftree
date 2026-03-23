# swiftratio

Visualize the Swift vs Objective-C file distribution in a hybrid iOS codebase as an interactive treemap.

## Examples

![image](https://github.com/eev25/swiftratio/blob/main/examples/vlc.png)
![image](https://github.com/eev25/swiftratio/blob/main/examples/wikipedia.png)
![image](https://github.com/eev25/swiftratio/blob/main/examples/wordpress.png)

## Overview

`swiftratio` recursively scans a directory, counts `.swift` and Objective-C (`.h`, `.m`) files per folder, and renders an interactive [Plotly Treemap](https://plotly.com/python/treemaps/) saved to `migration_progress.html`.

**Color encoding:**
- Blue — Swift-heavy (migration complete)
- White — equal mix
- Red — Objective-C-heavy (migration needed)

Each cell displays the directory name and lists the Objective-C files it contains directly, so files that need conversion are visible at a glance. Hovering over a cell shows the Swift/ObjC counts and percentages for that subtree.

## Usage

```
swiftratio <directory>
```

**Example:**

```sh
./swiftratio /path/to/wikipedia-ios
# → Saves migration_progress.html and opens it in the default browser
```

**Options:**

```
positional arguments:
  directory   Root directory to analyse

options:
  -h, --help  show this help message and exit
```

## Output

`migration_progress.html` — a self-contained interactive HTML file. The title shows the project name and overall Swift/Objective-C split (e.g. `wikipedia-ios — Swift: 67%, Objective-C: 33%`).

## Requirements

- [uv](https://docs.astral.sh/uv/) — dependencies (`plotly`) are declared inline via [PEP 723](https://peps.python.org/pep-0723/) and installed automatically on first run.

