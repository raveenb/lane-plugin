# /check-voice — Brand Voice Check

Evaluate whether a piece of text matches the user's brand voice.

## Steps

1. **Identify the brand**
   - If not specified, call `listBrands` and ask which brand

2. **Get voice data**
   - Call `checkBrandVoice` with the brand ID and the text to evaluate
   - This returns voice guidelines, content pillars, and sample phrases

3. **Analyze alignment**
   Compare the provided text against:
   - **Tone attributes** — Does it match the brand's formal/casual, technical/simple spectrum?
   - **Style dos and don'ts** — Does it follow the brand's writing rules?
   - **Vocabulary** — Does it use language consistent with the brand's sample phrases?
   - **Personality** — Does it reflect the brand's personality traits?

4. **Provide feedback**
   - Give an overall voice alignment score (Strong / Good / Needs Work)
   - List 2-3 specific things that match well
   - List 2-3 specific things that could be improved
   - Offer a revised version that better matches the brand voice

## Arguments
- `brand` (optional) — Brand name to check against
- `text` (required) — The text to evaluate, or paste it after running the command
