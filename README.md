# Flowchart Creator for Codex

This repository is a Codex plugin marketplace containing the `flowchart-creator` skills-only plugin. It creates editable flowcharts, decision trees, process maps, workflow diagrams, and code-flow diagrams.

## Publish this repository

1. Create a GitHub repository.
2. Upload or commit this repository's contents without changing the directory structure.
3. Replace `OWNER/REPOSITORY` in the commands below with the GitHub repository name.

## Install from GitHub

Recipients can add the marketplace and install the plugin with:

```powershell
codex plugin marketplace add OWNER/REPOSITORY
codex plugin add flowchart-creator@flowchart-tools
```

Then start a new Codex task so the newly installed skill is available.

For a private GitHub repository, recipients must already have Git access to the repository on their machine.

## Repository layout

```text
.agents/plugins/marketplace.json
plugins/flowchart-creator/.codex-plugin/plugin.json
plugins/flowchart-creator/skills/flowchart-creator/SKILL.md
```

The marketplace name is `flowchart-tools`, and the plugin name is `flowchart-creator`.
