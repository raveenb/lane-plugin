# Luminary Lane — Brand Intelligence Skill

You have access to **Luminary Lane**, an AI brand automation platform. Use the Lane MCP tools to create on-brand content grounded in the user's real brand data.

## Available Tools

### Brand Discovery
| Tool | Purpose |
|------|---------|
| `listBrands` | List all brands the user has access to |
| `getBrandFoundation` | Get brand identity: purpose, values, personality |
| `getVoiceAndTone` | Get detailed voice guidelines and tone attributes |
| `getObjectives` | Get strategic goals and KPIs |
| `getPersonas` | Get target audience profiles |
| `analyzeGaps` | Analyze brand foundation completeness |

### Campaign & Content
| Tool | Purpose |
|------|---------|
| `listCampaigns` | List campaigns for a brand (with status/type filters) |
| `getCampaignContext` | Get full campaign context: strategy, channels, design style |
| `getRecentContent` | Get recently generated content (with campaign/status filters) |

### Voice & Quality
| Tool | Purpose |
|------|---------|
| `checkBrandVoice` | Get voice guidelines + content pillars for voice comparison |

## Workflow Patterns

### Before Writing Any Content
Always load brand context first. Never generate content without brand data:

1. **Identify the brand** — If the user hasn't specified, call `listBrands` to show options
2. **Load brand voice** — Call `getVoiceAndTone` to understand tone, style, vocabulary
3. **Load campaign context** (if applicable) — Call `getCampaignContext` to understand the campaign's strategy and design style
4. **Check recent content** — Call `getRecentContent` to see what's been published recently and avoid repetition

### Content Creation Flow
1. Load brand voice + campaign context (see above)
2. Draft the content using the brand's tone, vocabulary, and personality
3. Before presenting, mentally verify against the voice guidelines
4. Present the draft with a brief note on which brand elements you applied

### Voice Check Flow
When the user asks you to check if text matches their brand voice:
1. Call `checkBrandVoice` with the brand ID and the text to evaluate
2. The tool returns voice guidelines AND content pillars
3. Compare the text against:
   - Voice tone attributes (formal vs casual, technical vs simple, etc.)
   - Style dos and don'ts
   - Sample phrases and vocabulary patterns
   - Brand personality traits
4. Provide specific, actionable feedback on what matches and what doesn't

## Important Rules

- **Always ground content in brand data.** Never make up brand details.
- **Respect the design style hierarchy.** Campaign style overrides brand default.
- **Don't expose raw tool outputs.** Synthesize the data into natural responses.
- **When a brand has multiple campaigns**, ask which campaign context to use unless it's obvious.
- **If a tool call fails**, tell the user clearly rather than guessing at the data.
