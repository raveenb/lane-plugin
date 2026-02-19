# /draft-post — Draft a LinkedIn Post

Draft a LinkedIn post using the user's brand voice and campaign context.

## Steps

1. **Identify brand and campaign**
   - If not specified, call `listBrands` and ask which brand
   - Call `listCampaigns` for the brand to find the active campaign
   - If multiple active campaigns, ask which one

2. **Load context**
   - Call `getVoiceAndTone` for the brand's voice guidelines
   - Call `getCampaignContext` for the campaign's strategy, objective, and design style
   - Call `getRecentContent` with `campaignId` to see recent posts (avoid repetition)

3. **Draft the post**
   - Match the brand's tone attributes (formal/casual, technical/simple, etc.)
   - Align with the campaign's objective and messaging strategy
   - Respect the effective design style (campaign overrides brand default)
   - Keep LinkedIn formatting best practices: hook line, short paragraphs, clear CTA
   - Suggest 3-5 relevant hashtags based on brand and campaign context

4. **Present the draft**
   - Show the post text
   - Note which brand voice elements you applied
   - Offer to adjust tone, length, or focus

## Arguments
- `brand` (optional) — Brand name to use
- `campaign` (optional) — Campaign name to target
- `topic` (optional) — Specific topic or angle for the post
