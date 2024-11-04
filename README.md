# Ansible Lint and Refactor

This action runs Ansible Lint on your playbooks and tasks, and then uses Aider to refactor them. It requires an image with Ansible, Ansible Lint, and Aider installed.

## Usage

To use this action in another repository, you can add the following code to your `action.yml` file:

```yaml
name: 'Ansible Lint and Refactor'
description: 'A Github action for fixing Ansible-lint failures and refactoring Ansible playbooks and tasks.'
author: 'Tosin Akinosho tosin.akinosho@gmail.com'
branding:
  icon: 'box'
  color: 'green'

runs:
  using: 'docker'
  image: 'docker.pkg.github.com/tosin2013/ansible-lint-and-refactor/ansible-lint-and-refactor:latest'

env:
  OLLAMA_API_BASE: 'http://ollama.ollama.svc.cluster.local:11434'
  MODEL: 'ollama/granite3-dense:8b'
  EDITOR_MODEL: 'ollama/granite3-dense:8b'
  PLAYBOOKS_DIR: 'playbooks/'
  TASKS_DIR: 'playbooks/tasks/'

jobs:
  ansible-lint-and-refactor:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Run Ansible Lint and Refactor
      run: |
        chmod +x /opt/ansible-venv/bin/ansible-lint-script.sh
        /opt/ansible-venv/bin/ansible-lint-script.sh
```

**Note**: Replace the `OLLAMA_API_BASE` URL with the URL of your own Ollama API.

## Inputs

None.

## Outputs

None.

## Environment Variables

- `OLLAMA_API_BASE`: The URL of the Ollama API.
- `MODEL`: The Ollama model to use for refactoring.
- `EDITOR_MODEL`: The Ollama editor model to use for refactoring.
- `PLAYBOOKS_DIR`: The directory containing your playbooks.
- `TASKS_DIR`: The directory containing your tasks.
