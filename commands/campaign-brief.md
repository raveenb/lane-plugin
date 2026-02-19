# /campaign-brief — Campaign Context Brief

Generate a comprehensive brief for a campaign, combining brand and campaign data into an actionable summary.

## Steps

1. **Identify brand and campaign**
   - If not specified, call `listBrands` and ask which brand
   - Call `listCampaigns` for the brand to find campaigns
   - If multiple campaigns, ask which one (or show all active)

2. **Load full context**
   - Call `getCampaignContext` for campaign strategy, channels, and design style
   - Call `getBrandFoundation` for the brand's purpose, values, and personality
   - Call `getPersonas` for audience profiles
   - Call `getRecentContent` with `campaignId` to see content history

3. **Present the brief**
   Structure the output as:

   **Campaign Overview**
   - Name, status, objective, date range
   - Campaign type and design style (note if inherited from brand)

   **Brand Context**
   - Brand purpose and key values
   - Voice tone summary (2-3 key attributes)
   - Target audience highlights

   **Content Strategy**
   - Active channels and their configurations
   - Content themes and angles to cover
   - Recent content summary (what's been covered, what gaps exist)

   **Recommendations**
   - Suggested next topics based on gaps in recent content
   - Tone reminders specific to this campaign

## Arguments
- `brand` (optional) — Brand name
- `campaign` (optional) — Campaign name
