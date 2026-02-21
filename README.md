# Luminary Lane — Claude Cowork Plugin

Brand intelligence for Claude. Draft on-brand content, check voice alignment, and generate campaign briefs — all powered by your real brand data from [Luminary Lane](https://luminarylane.app).

## Prerequisites

Before installing this plugin, you need:

1. **A Luminary Lane account** — Sign up at [luminarylane.app](https://luminarylane.app)
2. **At least one brand** set up with voice and tone guidelines
3. **Claude Desktop** (with Cowork access)

## Setup

### Step 1: Generate an API Key

1. Go to [app.luminarylane.app/profile/api-keys](https://app.luminarylane.app/profile/api-keys) and sign in
2. Click **Generate New Key**
3. Copy the key (starts with `ll_mcp_`) — you won't be able to see it again

### Step 2: Install the Plugin

In Claude Desktop, install the plugin from GitHub:

```
https://github.com/raveenb/lane-plugin
```

### Step 3: Configure the MCP Connection

Since this plugin uses API key authentication (not OAuth), you need to add the MCP server config to your Claude Desktop settings.

**On macOS**, edit `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "lane": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.luminarylane.app/mcp",
        "--header",
        "X-API-Key:${LANE_API_KEY}"
      ],
      "env": {
        "LANE_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

Replace `YOUR_API_KEY_HERE` with the key you generated in Step 1.

**On Windows**, the config file is at `%APPDATA%\Claude\claude_desktop_config.json`.

### Step 4: Restart Claude Desktop

Quit and reopen Claude Desktop for the MCP connection to take effect.

### Step 5: Verify

Open a new Cowork conversation and try:

```
/draft-post brand=YourBrandName topic=product launch
```

If you see Claude loading your brand's voice and tone data, you're all set.

## Commands

### `/draft-post` — Draft a LinkedIn Post

Creates a post using your brand's voice, tone, and active campaign context.

```
/draft-post brand=Acme topic=product launch
/draft-post brand=Acme campaign=Q1Launch
/draft-post                              # interactive — asks which brand
```

### `/check-voice` — Brand Voice Check

Evaluates whether a piece of text matches your brand voice and provides a revised version.

```
/check-voice brand=Acme text="Your draft copy here..."
/check-voice brand=Acme                  # then paste your text
```

Returns:
- Alignment score (Strong / Good / Needs Work)
- What matches well
- What could be improved
- A revised on-brand version

### `/campaign-brief` — Campaign Context Brief

Generates a structured brief combining brand foundation, campaign strategy, and content recommendations.

```
/campaign-brief brand=Acme
/campaign-brief brand=Acme campaign=Q1Launch
```

## Auto-Activation

When you discuss marketing or content creation topics in a Cowork conversation, the plugin automatically activates and offers to load your brand data. You don't need to use a slash command — just describe what you need.

> "I need to write a social media post for our product launch next week"

Claude will recognize this as a marketing task, list your brands, and load the relevant context.

## Troubleshooting

### "Brand not found"
The brand name must match exactly as it appears in your Lane dashboard. Run `/draft-post` without arguments to see your available brands.

### MCP tools not appearing
- Make sure `claude_desktop_config.json` is saved and Claude Desktop has been restarted
- Check that your API key starts with `ll_mcp_` and was copied correctly
- Verify the MCP server is reachable: `curl https://mcp.luminarylane.app/health`

### "Too many concurrent sessions"
This can happen if you have multiple Claude Desktop windows open. Close unused windows or wait a few minutes for stale sessions to expire.

### "Authentication failed"
Your API key may be invalid or revoked. Generate a new one at [app.luminarylane.app/profile/api-keys](https://app.luminarylane.app/profile/api-keys).

## What's Next

This is the MVP version of the Lane plugin. We're working on:
- OAuth support (no manual config needed)
- Content scheduling and publishing from within Claude
- Brand asset management (logos, colors, visual identity)
- Multi-channel content adaptation

## Links

- [Luminary Lane](https://luminarylane.app) — AI Brand Automation Platform
- [Report an issue](https://github.com/raveenb/lane-plugin/issues)
