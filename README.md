# NewUU Robotics Internship

Tasks, schedule and deliverables of the robotics internship at the School of Engineering, New Uzbekistan University. The work is done on the Unitree G1 humanoid and the Go2 quadruped: simulation, policy training and supervised tests on real hardware.

📖 **Read the site:** https://newuu-engineering.github.io/internship/

## What is in here

| Section | What it covers |
| --- | --- |
| [Schedule and deliverables](docs/tasks/interns.md) | Work packages by week, level and the deliverable for each |
| [Junior track](docs/tasks/junior.md) | Task 1: human motion to the G1 in MuJoCo, and a walking policy that walks in a circle |
| [Senior track](docs/tasks/senior.md) | Task 2: a Go2 locomotion policy in Isaac Lab, a wider command range and what it changes |

The site is built with Material for MkDocs on the NewUU documentation template, published to GitHub Pages, in English and Russian (pages without a translation fall back to English).

## Run it locally

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve   # http://127.0.0.1:8000
```

Before pushing, check that nothing is broken:

```bash
mkdocs build --strict   # broken links and missing files become errors
```

## Publishing

A push to `main` runs the **Deploy docs** workflow, which builds the site with `--strict` and publishes it to the `gh-pages` branch.

## Repository layout

| Path | What it is |
| --- | --- |
| `docs/` | The pages of the site; `page.ru.md` is the Russian version of `page.md` |
| `docs/tasks/` | Schedule and the two task tracks |
| `docs/includes/` | Shared snippets pulled into pages with `--8<--` |
| `docs/stylesheets/newuu.css` | The NewUU theme |
| `DESIGN-DECISIONS.md` | Why the theme looks the way it does |
| `CONTRIBUTING.md` | How to propose changes |

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Do not change the theme casually: if you find a gap in it, open an issue against the [documentation template](https://github.com/NewUU-engineering/newuu-docs-template) so the fix reaches every site.

## Licence

Content is CC BY 4.0. The university logo and mark in `docs/assets/` are not covered by that licence and remain the property of New Uzbekistan University.
