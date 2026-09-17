# devnet-template
This template repository provides a starting point for creating or importing repos in the CiscoDevNet organization on GitHub.com. 

Use this template as a guide to create a repo that encourages contributions and demonstrates thoughtful maintenance strategies.

Add source code, and in template files (`CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`), change `<project name>` to the repo name reference (e.g., `go-ciscosecureaccess`)
The source files need to have copyright and license headers:

For projects with Apache 2.0 license:

```python
# Copyright 2026 Cisco Systems, Inc. and its affiliates
#
# SPDX-License-Identifier: Apache-2.0
```
For projects with MIT license:

```python
# Copyright 2026 Cisco Systems, Inc. and its affiliates
#
# SPDX-License-Identifier: MIT
```

You can use the `reuse` tool to add copyright and license headers to all source files.

Examples of adding headers to `go` files:
```bash
docker run --rm --volume $(pwd):/data fsfe/reuse annotate --copyright-prefix string --copyright "Cisco Systems, Inc. and its affiliates" -l "Apache-2.0" --skip-existing **/*.go 
```


The `CODE_OF_CONDUCT.md` reflects our standards for interaction. 

The `CONTRIBUTING.md` file instructs new contributors on how to communicate with the project maintainers, report issues, provide pull requests, reviewing contributions, and how to version control releases.

The `LICENSE` file should contain the license you intend for the source code in the repo. 

The `SECURITY.md` file describes security policies and procedures including reporting a security-related bug and the policy on disclosure. 

The `AGENTS.md` file contains a template for guiding AI agents that work with your repository.

The `CONTRIBUTING_SKILLS.md` file is optional and contains a guide to adding related Agent Skills to the repository and [Cisco DevNet central skills repo](https://github.com/CiscoDevNet/skills/). The `SKILLS_TEMPLATE.md` contains the Agent Skill template file.
