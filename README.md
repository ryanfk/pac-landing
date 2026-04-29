# PAC Landing Page — build artifacts

Everything needed to ship the **PAC landing page** + **Follow the PAC** mailer feed in Helm. Built using the `pac:brand-identity` skill and brand colors sampled from the latest flyer (`PACFlyer-OpeningAnnouncement-5-3.png`).

## Layout

```
landing-page/
├── README.md                          ← you are here
├── content/
│   └── landing-page.md                ← page structure, micro-copy, anti-content
├── helm-config/
│   ├── brand-tokens.json              ← colors + typography for Helm project settings
│   └── follow-the-pac-feed.json       ← mailer feed spec, welcome email, template
└── assets/
    ├── flyer-hero.png                 ← latest flyer, page hero
    └── flyer-hero-low.jpg             ← lighter JPEG fallback for slow connections
```

## What's actually being built

1. **A landing page** at (TBD URL — `pac.immaculateconception.org` or hosted in Helm) that is essentially the latest flyer + a single email signup form. No mission statement, no values list — PAC's values are *implicit in what it is*.

2. **A Helm mailer feed** named **Follow the PAC** (slug `follow-the-pac`) that the landing page signup form subscribes to. Roughly one email per month before each PAC.

3. **PAC project branding** in Helm updated with colors and typography sampled from the actual flyer. See `helm-config/brand-tokens.json`.

## Voice / brand reference

The `pac:brand-identity` skill (in `../immaculate-plugin-marketplace/plugins/pac/skills/brand-identity/`) is the source of truth for tone, messaging, and anti-patterns. Apply it to any new copy.

Key non-negotiables for this page:

- Cream ground, navy + burnt orange, no pastels, no Comic Sans, no clip-art saints.
- Implicit values: PAC says what it *is*, not what it *means*.
- Logistics every time: "after the 9:30 Mass" + "in the gym."
- Contribution framing on closers, not consumption framing.
- No half-platitudes ("all are welcome," "faith journey," etc.).

## Execution path

The Helm MCP server is connected at `https://helmcode.dev/mcp` per `claude mcp list`, but its tools were not visible in the current session's tool registry. To apply this work to Helm:

**Option A — restart Claude Code, then push via MCP:**

1. Restart Claude Code so the helm MCP tools surface in the tool registry.
2. From a fresh session, ask Claude to "apply the PAC landing-page artifacts to the Helm pac project." Claude will use `create_feed`, `update_project_settings` (or equivalent), and the marketing-module / static-site tooling to push everything.

**Option B — apply manually via the Helm Dashboard:**

1. **Branding** — open the PAC project in the Helm Dashboard, paste the values from `helm-config/brand-tokens.json` into the project's branding / theme settings.
2. **Mailer feed** — Marketing > Feeds > Create. Use the `feed` block from `helm-config/follow-the-pac-feed.json`.
3. **Welcome email** — Marketing > Scheduled Emails (or transactional / autoresponder, depending on what's wired in PAC's project). Use `welcome_email` from the same JSON.
4. **Landing page** — depends on which marketing module hosts PAC's public page; use `content/landing-page.md` as the build spec, with `assets/flyer-hero.png` as the hero image.
