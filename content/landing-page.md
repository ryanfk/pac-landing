# PAC Landing Page — content spec

Implicit-values build. The page is the flyer + a way to follow along. No manifesto, no value statements, no "here's why we built this." The brand shines through what PAC *is* and how it *says* what it is.

**Suggested URL:** `pac.immaculateconception.org` (vanity) → or `helmcode.dev/.../pac` if hosted on Helm

---

## Page structure (top to bottom)

### 1. Hero — the flyer

The flyer is the page. Display `assets/flyer-hero.png` full-width on desktop (max-width ~700px, centered) and full-bleed on mobile. The flyer already carries the headline, the subhead, the tagline, the logistics, the illustration, and the call to expect. Don't redraw it as HTML — just present it.

- **Alt text:** *"THE PAC — A play-based social gathering for young families at Immaculate Conception. Faith, Family, Fellowship & Fun. Right after the 9:30 Mass in the gym. Next gathering: 5/3."*
- **Below flyer (small caption, optional):** *Click to download the printable version.* (Link to PDF/PNG.)

### 2. Follow-the-PAC signup — the only interactive element

Single block under the flyer. Heading + one-paragraph framing + form + reassurance.

**Heading (display type, burnt orange on cream):**

> **FOLLOW THE PAC**

**One-line framing (cream on navy or navy on cream — body type):**

> Get the next date, time, and what-to-bring straight to your inbox. About one email a month. No fluff.

**Form fields:**

- First name *(optional, single line — used for `{first_name}` substitution)*
- Email *(required)*
- Submit button: **`COUNT ME IN`** (display type, burnt orange button on cream, or cream button on navy)

**Below the form (small, cream/navy body):**

> One click to unsubscribe whenever. We'll never share your address.

### 3. Logistics block — text echo of the flyer (for SEO + accessibility)

Below the form, in regular-but-readable body type. This block exists so search engines and screen readers have the text content; sighted users mostly absorbed it from the flyer.

```
WHERE     Immaculate Conception Gym, East Aurora, NY
WHEN      Right after the 9:30 Mass on select Sundays
WHO       All ages — kids run, parents talk, families meet
COST      None
NEXT      May 3, 2026
```

### 4. Tiny footer

One line. Cream on navy.

> The PAC · A young-families gathering at Immaculate Conception, East Aurora, NY · Questions? `faith.formation@immaculateconception.org`

---

## What's intentionally NOT on this page

The user instruction is explicit: PAC lives its values implicitly, not explicitly. Do **not** add:

- A "mission" or "values" section.
- "Why we built PAC" / "The formation gap" — that's the strategic-voice register and belongs in parish-leadership memos, not on the public page.
- A list of organizers, board members, or clergy quotes (yet).
- Testimonials. Premature, and shifts the register toward marketing-y.
- Social proof counters ("40 kids! 20 families!") on the public page. Real, but not the right move on the public landing — it can creep in later as natural recap content.
- Donation / volunteer asks. Wrong page; PAC is friction-removal first.
- "Faith journey" / "all are welcome" / any of the platitudes from the brand anti-patterns.

The page should feel like the flyer — warmly direct, vintage-Americana, no apologetic preamble.

---

## Tone of micro-copy

The few words of HTML body copy on this page (form labels, button, reassurance line, footer) should pass the brand-identity public-facing voice check:

| Element | On-brand | Off-brand |
|---------|---------|-----------|
| Submit button | `COUNT ME IN` | "Subscribe to our newsletter" |
| Reassurance line | "About one email a month. No fluff." | "We respect your privacy and will only send valuable content." |
| Email confirmation | "You're on the list. See you in the gym." | "Thanks for subscribing! We'll be in touch soon." |
| Unsub line | "One click to unsubscribe whenever." | "You can manage your email preferences at any time." |

---

## Visual implementation notes

Apply `helm-config/brand-tokens.json` as the page's design tokens. Ground in cream `#EFD7A4`, anchor with navy `#0A3F58`, accent burnt orange `#D2580A`, golden yellow `#F5C84A` for stars/hovers.

- Page background: cream
- Flyer sits on cream — no extra frame
- Signup form: navy block on cream, or cream block with navy borders. Either works.
- Display type for headings: vintage slab (Alfa Slab One / Rye / Bevan) — see typography tokens
- Body / labels: humanist sans (Gill Sans / Avenir Next / fallback Source Sans)
- Star motifs (golden yellow) sparingly — one at the top of the form block, e.g.

---

## Confirmation page / success state

After submit, replace the form with:

> ★ **YOU'RE ON THE LIST.**
>
> See you in the gym after the 9:30. Watch for the next note.
>
> *(In the meantime — tell another family.)*

That last line is the only soft contribution-prompt on the page. Honors the brand pillar without belaboring it.
