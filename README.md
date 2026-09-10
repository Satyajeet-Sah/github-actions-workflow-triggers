# GitHub Actions Workflow Triggers

This repository demonstrates different **GitHub Actions workflow triggers, contexts, and GitHub-hosted runners** through simple workflow examples.

## Workflows

### 1. Events Workflow — `events.yaml`

Demonstrates different events that can trigger a GitHub Actions workflow:

- `workflow_dispatch` — Manually trigger the workflow
- `push` — Trigger when code is pushed to the repository
- `pull_request` — Trigger when a Pull Request is opened or updated
- `schedule` — Trigger the workflow based on a cron schedule

```yaml
on:
  workflow_dispatch:
  push:
  pull_request:
  schedule:
    - cron: "*/2 * * * *"
```

The workflow uses `${{ github.event_name }}` to display which event triggered the workflow.

#### Example Output

```text
My trigger is push event
My trigger is pull_request event
My trigger is workflow_dispatch event
My trigger is schedule event
```

---

### 2. Contexts Workflow — `contexts.yaml`

Demonstrates how to access **GitHub Actions context information**.

It uses the following expressions:

```yaml
${{ github.event_name }}
${{ github.event.action }}
${{ toJson(github.event) }}
```

This workflow displays:

- Event name
- Event action
- Complete event payload

This helps understand the information GitHub provides to a workflow when an event occurs.

---

### 3. Runners Workflow — `runner.yaml`

Demonstrates the use of a **GitHub-hosted runner**.

The workflow runs on:

```yaml
runs-on: ubuntu-latest
```

It displays runner information using environment variables:

```bash
$RUNNER_NAME
$RUNNER_OS
$RUNNER_ARCH
```

#### Example Output

```text
Workflow is executing on a GitHub-hosted runner.
Runner Name: GitHub Actions runner
Runner OS: Linux
Runner Architecture: X64
```

---

## Workflow Trigger Flow

```text
GitHub Event
    |
    +-- push
    |
    +-- pull_request
    |
    +-- workflow_dispatch
    |
    +-- schedule
            |
            v
    GitHub Actions Workflow
            |
            v
           Job
            |
            v
    GitHub-hosted Runner
            |
            v
       Execute Steps
```

## Learning Objectives

This repository is created to understand:

- GitHub Actions workflow triggers
- `workflow_dispatch`
- `push` events
- `pull_request` events
- Scheduled workflows using cron
- GitHub Actions contexts
- GitHub event payloads
- GitHub-hosted runners
- Runner environment variables
- `${{ github.event_name }}`
- `${{ github.event.action }}`

## Repository Structure

```text
.github/
└── workflows/
    ├── contexts.yaml
    ├── events.yaml
    └── runner.yaml

README.md
```

## Technologies

- Git
- GitHub
- GitHub Actions
- YAML
- Linux
- GitHub-hosted runners
