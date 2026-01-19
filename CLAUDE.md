# Propel Ops Roadmap

## Project Purpose
Interactive timeline visualization for Propel Health operations projects. Shows an 18-month view of onboarding, integration, and feature projects with status tracking and dependencies.

## Owner Context
- Solo developer (no separate front-end/back-end team)
- Familiar with R, learning Python — explain Python concepts with R comparisons where helpful
- Aviation background — aviation analogies work well for complex concepts
- This is a READ-ONLY visualization — project management happens via MCP tools

## Tech Stack
- **HTML/CSS**: Generated static timeline visualization
- **GitHub Pages**: Deployment target
- **MCP Tools**: Project CRUD operations
- **SQLite**: Data stored in unified Propel Health database

## File Organization
```
propel-ops-roadmap/
├── README.md               # User documentation
├── CLAUDE.md               # This file
├── templates/
│   └── roadmap-base.html   # HTML template for generation
└── docs/
    └── index.html          # Generated roadmap (GitHub Pages)
```

## Project Types

| Type | Description | Color |
|------|-------------|-------|
| `onboarding` | Clinic onboarding projects | Blue |
| `integration` | System integrations | Green |
| `feature` | Feature development | Purple |
| `migration` | Data migrations | Orange |
| `nccn` | NCCN guideline implementations | Teal |
| `maintenance` | Maintenance windows | Gray |
| `program_launch` | Program launches | Gold |

## Status Values

| Status | Styling | Description |
|--------|---------|-------------|
| `planned` | Dimmed | Future work, not started |
| `in_progress` | Solid | Active work |
| `completed` | Grayed out | Done |
| `on_hold` | Striped | Paused |
| `at_risk` | Red border | Needs attention |

## MCP Tools

All project management happens via MCP tools in propel_mcp:

| Tool | Description |
|------|-------------|
| `create_roadmap_project()` | Add a new project |
| `update_roadmap_project()` | Update project details |
| `list_roadmap_projects()` | List all projects with filters |
| `get_roadmap_project()` | Get detailed project info |
| `delete_roadmap_project()` | Remove a project |
| `add_roadmap_dependency()` | Create dependency between projects |
| `remove_roadmap_dependency()` | Remove a dependency |
| `generate_roadmap_html()` | Regenerate the HTML visualization |
| `push_roadmap_to_github()` | Push to GitHub Pages |

## Database Tables

Stored in the unified Propel Health database:

| Table | Description |
|-------|-------------|
| `roadmap_projects` | Main project data (name, dates, status, type) |
| `roadmap_project_clinics` | Project-clinic associations |
| `roadmap_dependencies` | Project dependencies (predecessor/successor) |
| `roadmap_holidays` | Holiday markers for timeline |
| `roadmap_config` | Timeline configuration (start date, months to show) |

## Visualization Features

- **18-month timeline**: Scrollable horizontal view
- **Color-coded bars**: By project type
- **Holiday markers**: Vertical lines for major holidays
- **Today indicator**: Red line showing current date
- **Hover tooltips**: Project details on hover
- **Status styling**: Visual distinction by project status

## Workflow

1. **Create projects** via MCP: `create_roadmap_project(name="Portland Onboarding", ...)`
2. **Update status** as work progresses: `update_roadmap_project(id=1, status="in_progress")`
3. **Regenerate HTML**: `generate_roadmap_html()`
4. **Deploy**: `push_roadmap_to_github()`

## Local Development

```bash
# Serve locally to preview
python -m http.server 8000 --directory docs/

# Then open http://localhost:8000
```

## Deployment

Hosted on GitHub Pages from the `docs/` directory:
1. MCP tool generates `docs/index.html`
2. Push to `main` branch
3. URL: `https://glewis05.github.io/propel-ops-roadmap/`

## Do NOT
- Edit `docs/index.html` directly — it's generated from template
- Add project data directly to HTML — use MCP tools
- Remove the today indicator or holiday markers
- Change the timeline scale without updating the generation template
