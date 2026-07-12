# Private Email Agent

**A private, AI email agent for business. Your inbox is handled, while every email and all AI processing stay on your own devices or infrastructure.**

Built by [ElephantClock](https://www.elephantclock.ae), a UAE technology company.

[**Learn more and book a private demo →**](https://www.elephantclock.ae/private-ai-email-agent.html)

---

Private Email Agent is a private AI email assistant that triages your inbox, summarizes long threads, drafts replies in your voice, tracks your commitments, and follows up on what matters. The difference from other AI email tools is where the intelligence runs: entirely on hardware you control. Email content never leaves your environment, because there is no third-party AI cloud to send it to.

This repository holds the product definition, the interaction and design system, and the in-progress Flutter MVP.

![Daily brief](mockups/intent/screens/desktop-brief.png)

## What it does

- **See only what needs you.** A short, ranked list of the decisions and risks that genuinely require your attention, each with the reason and the deadline.
- **Understand any thread in seconds.** A long, messy thread becomes a clear summary with the single next action.
- **Replies in your voice.** Drafts that answer every question, fit your tone, and avoid accidental commitments, ready for you to approve.
- **Nothing slips.** It remembers who owes you a reply and follows up within limits you set.
- **Never break a promise.** It detects the commitments you make in email and surfaces them before they become a missed deadline.
- **Protects you before you send.** Checks for the wrong recipient, a missing attachment, an accidental commitment, or a sensitive detail.

![Decision with evidence](mockups/intent/screens/desktop-decision.png)

## Private by architecture

Privacy here is enforced by the architecture, not promised in a policy.

- **Local AI model.** The model that reads and writes your email runs on your own devices or servers.
- **No third-party AI.** There is no external provider to send your mail to. Nothing to opt out of, and nothing to leak.
- **Works offline.** Triage, summaries, search, and drafting keep working without an internet connection.
- **Bounded autonomy.** The agent acts only within explicit, revocable permissions you grant, and it never sends consequential mail without your approval.
- **Auditable.** For anything it does, you can see what happened, why, which rule allowed it, and undo it where possible.

The trust and authority model is described in [docs/TRUST_MODEL.md](docs/TRUST_MODEL.md).

![Draft checked before sending](mockups/intent/screens/desktop-draft.png)

## How it is built

- **Flutter and Dart**, starting on macOS, with Android to follow.
- A small, firewalled architecture: a `MailProvider` seam (IMAP and SMTP behind it) and an `AiAnalyzer` seam (a local model behind it).
- Strict typed structures between the model and the UI. The model proposes; deterministic policy decides; the UI renders typed surfaces. The model never sends mail directly and never generates UI markup.
- Local model runtime over a loopback endpoint, with no network egress of email content.

The full architecture, contracts, safety model, and testing strategy are in [docs/MVP_PLAN.md](docs/MVP_PLAN.md).

## Repository layout

```
docs/      Product principles, brand, trust model, interaction and design system, intent catalog, MVP plan
mockups/   Interactive intent-native HTML prototype and screenshots (the visual specification)
app/       Flutter MVP (in progress)
```

### Documents

- [PRODUCT_SOUL.md](docs/PRODUCT_SOUL.md) — enduring product principles
- [TRUST_MODEL.md](docs/TRUST_MODEL.md) — authority levels and deterministic authorization
- [INTENT_UI.md](docs/INTENT_UI.md) — the conversation-first interaction model
- [INTENT_DESIGN_SYSTEM.md](docs/INTENT_DESIGN_SYSTEM.md) — visual, motion, and component system
- [USER_INTENTS.md](docs/USER_INTENTS.md) and [LOVABLE_INTENTS.md](docs/LOVABLE_INTENTS.md) — the intent catalog and the lovable subset
- [MEMORY_AND_PORTABILITY.md](docs/MEMORY_AND_PORTABILITY.md) — what the agent remembers and how it travels across devices
- [BRAND.md](docs/BRAND.md) — positioning and language
- [MVP_PLAN.md](docs/MVP_PLAN.md) — architecture, contracts, safety, testing

## Run the prototype

```bash
cd mockups
python3 -m http.server 4173
# open http://localhost:4173/intent/
```

## Status

In private preview. We are onboarding a first group of UAE businesses.

**[See how it works and book a private demo at elephantclock.ae →](https://www.elephantclock.ae/private-ai-email-agent.html)**

## License

Copyright © 2026 ElephantClock Technology. All rights reserved. See [LICENSE](LICENSE). This source is published for transparency and evaluation; it is not licensed for reuse.
