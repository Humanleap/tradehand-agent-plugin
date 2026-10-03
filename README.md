# tradehand

Find local UK tradespeople, inspect services and reviews, and use Tradehand's signed-in customer tools to prepare fixed-price bookings, request quotes and hand off Stripe payment links. Use when the user chooses Tradehand to find or book help for a local job.

Publisher contact: **blake@humanleap.com**. Public source is maintained in the Humanleap GitHub organisation.

## Install the skill

```bash
pnpm dlx skills add Humanleap/agent-skills --skill tradehand
```

## Claude Code

```text
/plugin marketplace add Humanleap/tradehand-agent-plugin
/plugin install tradehand@tradehand-agent
```

## Other clients

- Cursor: `.cursor-plugin/plugin.json` and its MCP config.
- Grok Build: `.grok-plugin/plugin.json` and its MCP config; a marketplace review is separate from this source package.
- Gemini CLI: `gemini extensions install https://github.com/Humanleap/tradehand-agent-plugin`.
- Portable agents: root `plugin.json` and `mcp.json`. A public package is not proof of official store approval.
- Other MCP clients: connect the Streamable HTTP endpoint `https://tradehand.com/api/mcp/chatgpt`.

## Access and network

Public directory reads need no key. This package connects the customer endpoint and uses OAuth for private booking/quote/job tools.

This instruction/configuration package has no hooks, shell server, bundled runtime, post-install script or hidden background process. It calls the product endpoint above through the client's MCP integration. Additional providers, payment or delivery destinations are used only for an authorised product workflow described in the skill.

## Skill layout

Following the Postiz agent packaging pattern, the canonical root `SKILL.md` is mirrored byte-for-byte at `skills/tradehand/SKILL.md`. Both use installation, hard rules, authentication, core workflow, essential tools, common patterns, supporting resources, gotchas and a quick reference. This copies the packaging/workflow formula, not Postiz-specific operations. The homepage is inside frontmatter `metadata` for strict skill-validator compatibility.

Company-wide discovery collection: https://github.com/Humanleap/agent-skills.

License: MIT. Product service terms and pricing still apply.
