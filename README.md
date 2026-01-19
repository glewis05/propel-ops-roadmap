# Propel Operations Roadmap

Interactive timeline visualization for Propel Health operations projects.

## Overview

This roadmap displays projects across an 18-month timeline with:
- Color-coded project bars by program
- Holiday markers
- Today indicator line
- Status-based styling (planned, in_progress, completed, on_hold, at_risk)
- Hover tooltips for project details

## Usage

The roadmap is generated from the propel-health MCP server database using:

```
generate_roadmap_html()
```

To push updates to GitHub Pages:

```
push_roadmap_to_github()
```

## MCP Tools

| Tool | Description |
|------|-------------|
| `create_roadmap_project()` | Add a new project to the roadmap |
| `update_roadmap_project()` | Update project details |
| `list_roadmap_projects()` | List all projects with filters |
| `get_roadmap_project()` | Get detailed project info |
| `delete_roadmap_project()` | Remove a project |
| `add_roadmap_dependency()` | Create dependency between projects |
| `remove_roadmap_dependency()` | Remove a dependency |
| `list_roadmap_dependencies()` | View all dependencies |
| `generate_roadmap_html()` | Regenerate the HTML visualization |
| `push_roadmap_to_github()` | Push to GitHub Pages |

## Project Types

- `onboarding` - Clinic onboarding projects
- `integration` - System integrations
- `feature` - Feature development
- `migration` - Data migrations
- `nccn` - NCCN guideline implementations
- `maintenance` - Maintenance windows
- `program_launch` - Program launches

## Status Values

- `planned` - Future work (dimmed)
- `in_progress` - Active work
- `completed` - Done (grayed out)
- `on_hold` - Paused (striped)
- `at_risk` - Needs attention (red border)

## Database Tables

- `roadmap_projects` - Main project data
- `roadmap_project_clinics` - Project-clinic associations
- `roadmap_dependencies` - Project dependencies
- `roadmap_holidays` - Holiday markers
- `roadmap_config` - Timeline configuration

## Generated Files

- `docs/index.html` - The roadmap visualization (GitHub Pages)
