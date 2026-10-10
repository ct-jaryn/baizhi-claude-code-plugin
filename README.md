# Baizhi Agent Toolkit community plugin

An optional Claude Code plugin that registers the Baizhi Agent Toolkit HTTP MCP
connection and an explicitly invoked research skill. Maintained by ct-jaryn;
no vendor or marketplace endorsement is implied. Submission to Tons of Skills
is a separate review process; this source is not an accepted Tons listing.

A Baizhi account and user-owned API key are required. Hosted usage may incur
charges. The MIT license covers this plugin's configuration and documentation,
not the hosted backend or its service terms.

## Install and configure

In Claude Code's interactive session:

```text
/plugin install baizhi-agent-toolkit --marketplace ct-jaryn/baizhi-claude-code-plugin
/plugin configure baizhi-agent-toolkit@baizhi-community
```

The one-step marketplace install form requires Claude Code 2.1.275 or later.
This plugin's native behavior was tested on 2.1.295; older hosts and other
platforms are not verified. Enter your key in the sensitive configuration
dialog, never in a prompt, command argument, Git file, log or research report.
The host substitutes `user_config.api_key` into the Authorization header.

Installing without the required value succeeds with a configuration warning;
the tested host does not register this MCP server until it is configured.
The CLI ignores an empty sensitive value after configuration and retains the
old value; do not treat that as removal or key revocation. To stop using the
plugin, disable or uninstall it; revoke a key through the service's account
controls when required. Local interruption does not prove remote cancellation
or that billing has stopped.

Endpoint: `https://agent-toolkit.app.baizhi.cloud/mcp`. Connecting contacts the
hosted service. Available tools, permissions and credits depend on the account.
The plugin contains no code to read credential files or log a key; its native
configuration and the hosted service have their own storage and security behavior.

## Use

Explicitly invoke `/baizhi-agent-toolkit:toolkit-research` with a public question
and an authorized maximum call or cost budget. For example:

- Compare three public sources with at most four tool calls.
- Research a public topic with a six-call limit; stop on a credit error.
- Inspect available tools without starting a research call.

The skill discovers current tools and schemas rather than hard-coding tool
names. Invoking it grants this plugin's configured MCP server for that turn,
subject to your overriding permission rules. Use only tools appropriate to the
approved task. This grant does not authorize paid usage. Budget, destination
and evidence checks are instructions, not a programmatic quota or citation validator.
Stop on authentication, permission or credit errors and use account controls.

## Installation and validation boundaries

This is a complete native plugin with inline MCP configuration and sensitive
`userConfig`. Copying only its SKILL.md with `tons skills install` does not
register that connection and is not equivalent setup. Other adapters are not
verified. No executables, agents, hooks or shell-command files are included.

The current Tons validator passed this candidate at marketplace tier, 99/100,
with no blocking errors or warnings. Actual isolated Claude Code 2.1.295
installation, skill loading, permission, sensitive-value substitution and tool
dispatch were tested against owned loopback MCP and deterministic model fixtures.
Those tests do not establish model reasoning, every workflow instruction,
production availability, paid-service quality or GUI behavior. Real Baizhi and
model requests in that validation were zero. See [validation details](docs/VALIDATION.md)
and [the PRD](docs/PRD.md).

## Sources and maintenance

- [Service and account information](https://agent-toolkit.app.baizhi.cloud)
- [Native plugin configuration](https://code.claude.com/docs/en/plugins-reference)
- [MCP specification](https://modelcontextprotocol.io/specification)

Preserve the personal author identity, MIT scope and native configuration when
mirroring. Source publication, source-list review, mirror sync, marketplace
availability, installation and production verification are separate stages.
