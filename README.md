# E-Web Internal Cowork Marketplace

Private plugin marketplace for E-Web Marketing's Claude Cowork team.

This repo distributes E-Web's custom Cowork plugins (slash commands, skills, and workflows) to every analyst's Cowork session. New analysts add the marketplace once on onboarding and get every plugin automatically — including future updates.

## Plugins in this marketplace

| Plugin | Version | Description |
|---|---|---|
| `eweb-ai-visibility-audit` | 0.1.0 | Run the full AI Visibility Audit workflow for a client — interactive SEMrush competitor discovery, data pull, branded DOCX + Gamma deck on the E-web Brand theme. |

## How to publish this marketplace (one-time setup, by the maintainer)

1. **Create a private Git repo** on GitHub / GitLab / Bitbucket / internal Git — call it `eweb-cowork-plugins` (or any name; the slug becomes part of the marketplace URL).
2. **Push this folder** to that repo:
   ```bash
   cd eweb-cowork-marketplace
   git init
   git add .
   git commit -m "Initial marketplace with eweb-ai-visibility-audit v0.1.0"
   git branch -M main
   git remote add origin git@github.com:<your-org>/eweb-cowork-plugins.git
   git push -u origin main
   ```
3. **Add team members as repo collaborators** (or an org team) so they have read access.
4. **Distribute the marketplace URL** in your team onboarding doc:
   - HTTPS: `https://github.com/<your-org>/eweb-cowork-plugins`
   - Or shorthand: `<your-org>/eweb-cowork-plugins`

## How analysts install plugins (each analyst, one-time on onboarding)

In any Cowork session, run:

```
/plugin marketplace add <your-org>/eweb-cowork-plugins
```

Then install any plugin from the marketplace:

```
/plugin install eweb-ai-visibility-audit
```

That's it — the slash command `/ai-visibility-audit` is now available in every Cowork session, and the plugin auto-loads its skill on natural-language triggers like "run an AI visibility audit for [client]".

## How updates flow to the team

When a plugin is updated:

1. The maintainer bumps the version in `plugins/<plugin-name>/.claude-plugin/plugin.json` AND in this `marketplace.json`.
2. Maintainer commits + pushes.
3. Each analyst runs `/plugin marketplace update` to pull latest manifests, then `/plugin install <plugin-name>` to upgrade.

Best practice: announce version bumps in your team Slack channel with a one-line changelog and the upgrade command.

## Onboarding integration

Add this paragraph to your **new-hire onboarding doc** (Confluence / Notion / Drive):

> **Cowork plugins (Day 1 setup)**
> 1. Open Cowork. Run: `/plugin marketplace add <your-org>/eweb-cowork-plugins`
> 2. Install the AI Visibility Audit workflow: `/plugin install eweb-ai-visibility-audit`
> 3. Verify by typing `/ai-visibility-audit` in any new conversation — Cowork should ask for a client URL.
> Future updates flow automatically — run `/plugin marketplace update` once a sprint to pick up the latest.

## Folder structure

```
eweb-cowork-marketplace/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace manifest (lists every plugin)
├── plugins/
│   └── eweb-ai-visibility-audit/ # Each plugin lives here as a sub-folder
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── commands/
│       ├── skills/
│       └── README.md
└── README.md                      # This file
```

## Adding a new plugin to the marketplace

1. Drop the new plugin folder under `plugins/<new-plugin-name>/`.
2. Add a new entry to the `plugins` array in `.claude-plugin/marketplace.json`.
3. Bump the marketplace `version` in `marketplace.json` (e.g. 1.0.0 → 1.1.0 for a new plugin).
4. Commit and push. Done.

## Maintainer

E-Web Marketing — Senior SEO Strategy Team
plugins@ewebmarketing.com.au
