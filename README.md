# keigo

**Say it blunt. Send it polished.**

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)

An agent skill that turns casual, blunt, or fragmentary Japanese into natural business Japanese (敬語) — the kind you can paste straight into an email and send unchanged. Built as a [`SKILL.md`](skills/keigo/SKILL.md), the portable skill format understood by Claude Code and other agent tools that support it.

[See it](#see-it) · [Install](#install) · [Usage](#usage) · [Tones](#tones) · [Notes & limits](#notes--limits) · [License](#license)

## See it

| Situation | You type | keigo sends |
|---|---|---|
| 催促 (chasing a reply) | `本件の進捗どう` | 本件の進捗につきまして、その後いかがでしょうか。ご多忙のところ恐れ入りますが、現在の状況をお知らせいただけますでしょうか。 |
| セールストークの拒否 (declining a pitch) | `今はいらない、まず無償版で試してみる` | せっかくのご提案ですが、今回は導入を見送らせていただき、まずは無償版を試してみたいと考えております。今後導入を検討する際には、改めてご連絡いたします。 |
| 発注見送り (going with a competitor) | `本件は予算面だから発注できない。残念だけどアルファ商事にする予定` | この度はご提案いただき、誠にありがとうございました。社内で検討いたしました結果、予算面の都合により、今回はアルファ商事にお願いする運びとなりました。誠に恐縮ですが、ご了承いただけますでしょうか。 |

No greeting, no sign-off, no filler — just the body, ready to send.

## Install

**Via the GitHub CLI** ([`gh skill`](https://cli.github.com/manual/gh_skill), public preview):

```bash
gh skill install y26805/keigo
```

**Via [`npx skills`](https://github.com/vercel-labs/skills):**

```bash
npx skills add y26805/keigo
```

**Manually:** copy `skills/keigo/SKILL.md` into your tool's skills directory. No dependencies either way.

## Usage

```
/keigo <input> [--situation <situation>] [--tone <tone_name>]
```

- **`<input>`** (required, positional): the casual/blunt Japanese message to rewrite.
- **`--situation <text>`** (optional): a short noun-phrase describing the business context (e.g. `催促`, `見積書の未受領`, `発注見送り（丁寧）`). If omitted, it's inferred from the input.
- **`--tone <name>`** (optional, default `shakaijin`): controls the register of the output. Accepts `-` or `_` as separators. Full mode names also work directly (e.g. `--tone megabank-compliance-mode`).

```
/keigo 時間合わない --situation 打ち合わせの再調整 --tone startup
```

## Tones

| Alias | Full name | Style |
|---|---|---|
| `megabank` | `megabank-compliance-mode` | Highly formal, conservative, deferential. Traditional honorifics, indirect requests. |
| `shakaijin` *(default)* | `proper-shakaijin-mode` | Natural, polished, professional. Register matches the situation. |
| `startup` | `startup-speed-mode` | Friendly, modern, energetic. Short and approachable; one `!` allowed where natural. |

## Notes & limits

- Concrete details (dates, times, names, numbers) are preserved verbatim; nothing is invented.
- Register adapts to audience: external messages get full keigo, internal/team messages are lighter.
- Japanese in, Japanese out — this rewrites register, it doesn't translate.
- `--tone` shapes formality and warmth, not content; it won't turn a refusal into an acceptance or vice versa.
- See [SKILL.md](skills/keigo/SKILL.md) for the full rewrite strategy, keigo rules, and model answers used to drive the rewrite.

## License

MIT
