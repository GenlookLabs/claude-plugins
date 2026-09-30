# Genlook plugins for Claude Code

## virtual-try-on

See any clothing, eyewear or accessory on a photo of a person, in about 10 seconds, straight from Claude Code. Connects the [Genlook MCP server](https://genlook.app/docs/tryon-api/mcp?utm_source=github&utm_medium=readme&utm_campaign=claude_plugin) and adds a skill that walks Claude through a try-on.

```bash
claude plugin marketplace add GenlookLabs/claude-plugins
```

```bash
claude plugin install virtual-try-on@genlook
```

Then run `/mcp` and sign in with your Genlook account. New accounts get 10 free credits; 1 credit per try-on.

Docs: https://genlook.app/docs/tryon-api/mcp?utm_source=github&utm_medium=readme&utm_campaign=claude_plugin · Try it in the browser: https://huggingface.co/spaces/Genlook/virtual-try-on?utm_source=github&utm_medium=readme&utm_campaign=claude_plugin
