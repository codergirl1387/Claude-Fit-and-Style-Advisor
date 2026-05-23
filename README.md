# Fit & Style Advisor

A Claude [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) that turns Claude into a personal online-shopping advisor. Share any clothing item — a photo, a product description, or a link — and the skill tells you whether it will **fit** you, whether the **color** suits you, and how to **style** it.

It is personalized: you give Claude a short profile once, and every assessment is judged against your body shape, height, size, and skin undertone.

---

## What it does

For each item you share, the skill produces:

1. **A verdict table** — six checks (size, silhouette, length, shoulders/neckline, fabric, color), each marked ✅ works, ⚠️ works with a fixable caveat, or ❌ skip.
2. **A one-line verdict** — the buy / skip call in a sentence.
3. **A styling table** — how to wear the item across eight settings (casual, workwear, date night, two party types, travel, transitional layering, and a wedding-guest row for occasion-wear). The styling table is shown **only when the verdict has no red flags** — if an item is a genuine no, the skill tells you why instead of styling a bad buy.

The skill works for all body shapes (hourglass, pear, apple, rectangle), all height bands (petite, average, tall), and all skin undertones (warm, cool, neutral).

## Example output

```
## Fit & Style Verdict: Empire-Waist Floral Maxi Dress — Mustard

**Overall: ⚠️ Works with caveats** — styling unlocked

| # | Check                        | Mark | Notes                                              |
|---|------------------------------|------|----------------------------------------------------|
| 1 | Size / measurements          | ✅   | L fits; empire seam skims the midsection           |
| 2 | Silhouette vs body shape     | ✅   | Empire waist draws the eye up — ideal for apple    |
| 3 | Length / proportion          | ⚠️   | Maxi on a 5'1" frame will pool; needs Petite/hem   |
| 4 | Shoulders / straps / neckline| ✅   | Empire bodice flatters; confirm a V or scoop neck  |
| 5 | Fabric / structure           | ✅   | Flowy floral skims rather than clings              |
| 6 | Color                        | ✅   | Mustard sits in a warm undertone's best range      |

**Buy it — but Petite or a hem is non-negotiable at 5'1".**
```

(Styling table follows when the verdict has no red rows.)

## Install

**Claude.ai (Pro, Max, Team, or Enterprise):**
1. Enable code execution: Settings → Capabilities.
2. Go to Customize → Skills.
3. Upload `fit-and-style-advisor` as a ZIP containing the `SKILL.md` file.
4. Confirm the skill is toggled on.

**Claude Code:**
- Personal use: copy the `fit-and-style-advisor` folder into `~/.claude/skills/`.
- Single project: copy it into `.claude/skills/` inside that project.

## How to use

1. Share a clothing item with Claude — paste a product link, upload a photo, or describe it.
2. The first time, Claude asks for your profile. Choose the **Quick** tier (body shape, height, size, undertone, style vibe) or the **Precise** tier (Quick plus exact measurements).
3. Claude returns the verdict table, the one-line verdict, and — if the item passes — the styling table.
4. Claude also gives you a reusable `MY FIT PROFILE` block. Paste it at the start of future chats, or save it in a Claude Project, to skip the intake next time.

## Privacy

Your measurements stay inside your own conversation with Claude. The skill does not store them, does not transmit them, and contains no personal data in the file itself. Share only what you are comfortable putting in a chat.

## Limitations

- A skill file cannot track time. The 6-month profile re-check works by reading the date in your pasted profile block — it is not an automatic timer.
- Some retailers (for example, Mango) load garment-measurement tables only after a click, which a page fetch may not capture. The skill falls back to the brand size chart and labels it an estimate.
- Fit advice is guidance, not a guarantee. Sizing varies by brand; check the retailer's size chart and return policy before buying.

## Contributing

Issues and pull requests are welcome — particularly test cases for body shapes, heights, or undertones that the current logic handles poorly.

## License

Released under the MIT License. See [LICENSE](LICENSE).
