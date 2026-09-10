# Contributing Cisco Agent Skills

> Here is a guide to adding related skills to your repository. If SKILLS is relevant to this repository, please follow this guide and add skills to this repo and to the [central skills repo](https://github.com/CiscoDevNet/skills/) for all products. SKILLS.md in this template should be deleted or edited to reflect open-source project content. 

This guide explains how to contribute a skill to
[`CiscoDevNet/skills`](https://github.com/CiscoDevNet/skills). Read the
[Agent Skills specification](https://agentskills.io) and this repository's
[authoring guide](https://github.com/CiscoDevNet/skills/blob/main/spec/authoring-guide.md) before starting.

## What belongs in this repository

Contributions should provide reusable, product-specific guidance for a Cisco
product, solution, or technology. Good skills cover a concrete workflow such
as safe configuration review, API automation, troubleshooting, validation, or
integration setup.

Each skill should:

- use current Cisco documentation, API schemas, SDK references, [MCP servers](https://developer.cisco.com/codeexchange/ai/MCP/), or installed
  CLI help;
- state supported product versions and prerequisites;
- begin operational workflows with read-only discovery;
- distinguish read-only, locally modifying, and remotely mutating actions;
- include rollback and before/after verification for changes;
- use placeholders instead of credentials, customer data, or private topology;
- be useful as a standalone folder without depending on local reference
  repositories.

Do not add empty skills, speculative API endpoints, unverified commands,
customer configurations, credentials, certificates, or paste-ready production
changes.

## Choose the product and skill names

Use lowercase kebab-case names.

- Product folder examples: `meraki`, `thousandeyes`, `cml`,
  `cloud-security`, `ise`, `aci`, `intersight`, `ios`, and `sccfm`.
- Skill folder examples: `cisco-ios-patterns`, `sccfm-cli`, or
  `sccfm-ansible`.

Add a new skill to an existing product folder when possible. Propose a new
product folder only when none of the existing namespaces accurately describes
the content.

## Create the skill

1. Fork and clone
   [`CiscoDevNet/skills`](https://github.com/CiscoDevNet/skills).
2. Create a branch for one product or coherent workflow.
3. Copy the template into a new folder:

   ```bash
   cp -R template/skill-template skills/PRODUCT_NAME/SKILL_NAME
   ```

4. Rename and edit the frontmatter so `name` exactly matches `SKILL_NAME` and
   `metadata.product` exactly matches `PRODUCT_NAME`.
5. Replace every template placeholder with reviewed content.
6. Add supporting files only when the skill uses them:

   ```text
   skills/PRODUCT_NAME/SKILL_NAME/
   ├── SKILL.md
   ├── scripts/       # optional executable helpers
   ├── references/    # optional detailed documentation
   └── assets/        # optional templates or static resources
   ```

Keep `SKILL.md` concise. Link directly to supporting files rather than adding
deeply nested documentation.

## Add the marketplace copy

Every canonical skill must have a byte-identical packaged copy:

```text
skills/PRODUCT_NAME/SKILL_NAME/SKILL.md
plugins/PRODUCT_NAME/skills/SKILL_NAME/SKILL.md
```

Copy the complete skill folder:

```bash
cp -R skills/PRODUCT_NAME/SKILL_NAME \
  plugins/PRODUCT_NAME/skills/SKILL_NAME
```

Do not edit the plugin copy separately. The validator rejects drift between the
canonical and packaged `SKILL.md` files.

When introducing a new product namespace, also add:

```text
skills/PRODUCT_NAME/README.md
plugins/PRODUCT_NAME/.claude-plugin/plugin.json
plugins/PRODUCT_NAME/README.md
```

Then register the product in both marketplace catalogs:

- `.claude-plugin/marketplace.json`
- `.agents/plugins/marketplace.json`

Do not change marketplace files when merely adding another skill to an existing
product plugin.

## Update the skill lists

Update the root [README](https://github.com/CiscoDevNet/skills/README.md) in the same pull request:

1. Add the new skill to the catalog summary or product list (Repo: https://github.com/CiscoDevNet/skills/).
2. Link the skill name to
   `skills/PRODUCT_NAME/SKILL_NAME/SKILL.md`.
3. Add an installation example only if it materially helps users.
4. Keep product namespaces with no reviewed `SKILL.md` clearly identified as
   scaffolds rather than available coverage.

If a new product namespace was added, also update
[`skills/README.md`](skills/README.md) and the namespace list in
[`spec/authoring-guide.md`](spec/authoring-guide.md).

## Sources and licensing

Prefer primary Cisco documentation:

- [Cisco support documentation](https://www.cisco.com/c/en/us/support/index.html)
- [Cisco developer and API documentation](https://developer.cisco.com/docs/)
- [Cisco DevNet Sandboxes](http://developer.cisco.com/sandbox/)

When importing or adapting existing content:

1. Confirm that its license permits redistribution.
2. Preserve required copyright and attribution notices.
3. Record the source URL, immutable commit or release, paths, license, and
   modification status in [`SOURCES.md`](https://github.com/CiscoDevNet/skills/blob/main/SOURCES.md).
4. Add any required third-party license text under `THIRD_PARTY_LICENSES/`.

## Security requirements

- Never commit passwords, API keys, tokens, private keys, authenticated
  connection strings, or generated customer data.
- Never ask users to paste secrets into chat. Use hidden prompts, operating
  system credential stores, or permission-restricted secret files.
- Treat generated device configuration as a candidate requiring operator
  review.
- Require exact targets, a rollback path, and explicit approval before
  mutating operations.
- If a skill uses certificates, require checks for validity dates, key
  strength, signature algorithm, hostname and chain trust, and intentional
  self-signing.
- Review security-sensitive guidance against
  [CoSAI Project CodeGuard](https://github.com/cosai-oasis/project-codeguard).

Report vulnerabilities according to [`SECURITY.md`](SECURITY.md), not through a
public issue.

## Validate the contribution

Run from the repository root:

```bash
python3 scripts/validate_skills.py
python3 -m json.tool .claude-plugin/marketplace.json >/dev/null
python3 -m json.tool .agents/plugins/marketplace.json >/dev/null
git diff --check
```

If Claude Code tooling is installed, also run:

```bash
claude plugin validate .
```

Review the output and resolve failures before opening a pull request. Test
mutating instructions only in an appropriate lab or
[Cisco DevNet Sandbox](http://developer.cisco.com/sandbox/), never against
production.

## Pull request checklist

- [ ] The skill has one clear purpose and concrete activation triggers.
- [ ] The folder name matches the frontmatter `name`.
- [ ] Product and skill names use lowercase kebab-case.
- [ ] Canonical and plugin copies are byte-identical.
- [ ] README skill lists and links are updated.
- [ ] Commands, endpoints, options, and versions are verified.
- [ ] Examples contain no credentials or customer data.
- [ ] Mutating workflows include targets, rollback, approval, and verification.
- [ ] Imported content is recorded in `SOURCES.md`.
- [ ] Repository validation passes.
- [ ] The pull request describes documentation sources, tested versions,
      validation performed, and any live-testing gaps.
