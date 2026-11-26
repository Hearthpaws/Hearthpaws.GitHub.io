# HearthPaws — premium pet storefront

A single-file, dependency-free English storefront for a **premium pet dropshipping store** selling into the US, Canada, the UK, Japan, South Korea and Singapore.
Open `index.html` in any browser — no build step, no CDN, no third-party script.

- Brand: **HearthPaws** — "Premium comfort for the pets who wait for you."
- Palette: cream / moss green / clay. Type: system serif display + system sans body.
- Product photography: **real supplier photos** from the live CJdropshipping listings, downloaded to
  `assets/` (760 × 760 JPEG, ~40–100 KB each) so the cards show the item that actually ships.
  Decorative art (hero, cart thumb for filters) remains hand-written inline SVG.
- Cart: slide-out drawer with quantity controls, subtotal, free-shipping meter ($50 threshold),
  localStorage persistence (`hearthpaws-cart-v2`), keyboard/Escape close, focus return.

> **Live checkout:** the drawer's "Checkout with PayPal" button posts a PayPal Cart Upload form
> (`cmd=_cart`, `business=chaeminleeandrew@gmail.com`, USD, $4.95 flat handling under $50) to
> `paypal.com/cgi-bin/webscr`, with `?checkout=success` / `?checkout=cancel` return states.
> Each cart line's `item_number` is now the **CJdropshipping SKU**, so a paid order can be pasted or
> mapped straight into a CJ order without a lookup table.
> No customer reviews are shown — the reviews section says "Verified reviews — coming soon".

---

## 1. Product lineup — one supplier, fourteen products

**Every purchasable item is a CJdropshipping product.** Orders can be fulfilled end-to-end from a
single CJ account (`CJ6093490`, `chaeminleeandrew@gmail.com`) with no second supplier.

**Pricing rule in force (2026-11-27, user instruction): net margin must be under 10% on every variant.**
Net = retail × 0.971 − 0.30 (PayPal 2.9% + $0.30) − landed cost. Nothing may sell at a loss, so each
retail price is the whole- or half-dollar step that lands between roughly 4% and 9%.

Landed cost = CJ item price **+ CJ shipping to a US address**, read from the live product page
("Total: $…", ship-to US, cheapest available method) on **2026-11-27** for every line below — the
whole table was re-measured that day, and several landed costs had moved since the 2026-11-22 figures
(CJ posted shipping-price adjustments on 23, 24 and 25 Nov).

| # | Product (store name) | CJ SKU | CJ item | CJ ship to US | Landed | Retail | Net after fees | Net margin |
|---|---|---|---|---|---|---|---|---|
| 1 | **The Haven Bed** — Medium 20 in (50 cm) | `CJJJCWMY01390-Grey50cm` | $5.61 | $19.60 | **$25.21** | $28 | $1.68 | 6.0% |
| 1 | **The Haven Bed** — Large 26 in (65 cm) | `CJJJCWMY01390-Grey 65cm` | $6.08 | $24.86 | **$30.94** | $35 | $2.75 | 7.8% |
| 2 | **SteamGroom 3-in-1** — Ceramic white | `CJYD207827101AZ` | $3.86 | $8.58 | **$12.44** | $14 | $0.85 | 6.1% |
| 2 | **SteamGroom 3-in-1** — Blush pink | `CJYD207827102BY` | $3.86 | $7.25 | **$11.11** | $13 | $1.21 | 9.3% |
| 3 | **Stillwater Fountain** — Circulation 2 L | `CJMY174605320TG` | $13.16 | $17.12 | **$30.28** | $34 | $2.43 | 7.2% |
| 3 | **Stillwater Fountain** — Motion-sense 2 L | `CJMY174605325YB` | $16.92 | $17.86 | **$34.78** | $39 | $2.79 | 7.2% |
| 4 | **The Pulse Tail** — Magic Tail red | `CJMY212708201AZ` | $0.95 | $5.16 | **$6.11** | $7 | $0.39 | 5.5% |
| 5 | **Trailhead Harness & Lead** — L, blue/mustard | `CJSB217533304DW` | $2.13 | $7.10 | **$9.23** | $10.50 | $0.67 | 6.3% |
| 6 | **Stillwater Maze Bowl** — slow feeder, green | `CJGY174846501AZ` | $1.29 | $8.80 | **$10.09** | $11.50 | $0.78 | 6.8% |
| 7 | **Fish Lick Mat** — teal silicone | `CJGY189089701AZ` | $7.98 | ≈$3.00 | **$10.98** | $12.50 | $0.86 | 6.9% |
| 8 | **Tumble Treat** — treat tumbler, 200 g | `CJYD196344901AZ` | $2.39 | $7.17 | **$9.56** | $11 | $0.82 | 7.5% |
| 9 | **Lure Pod** — feather teaser, pink | `CJYD235480702BY` | $3.25 | $7.37 | **$10.62** | $12 | $0.73 | 6.1% |
| 10 | **Sisal Scratch Mat** — L, natural | `CJMY107357801AZ` | $8.05 | $14.81 | **$22.86** | $26 | $2.09 | 8.0% |
| 11 | **Litter Trap Mat** — grey, 46 × 60 cm | `CJJCWMY00030-46x60cm-Foldable gray` | $4.68 | $8.93 | **$13.61** | $15.50 | $1.14 | 7.4% |
| 12 | **Carry-Out Cat Bag** — L, blue | `CJMY112580406FU` | $6.30 | $11.49 | **$17.79** | $20 | $1.33 | 6.7% |
| 13 | **TrailSip Bottle** — 800 ml, blue-grey | `CJJT171012401AZ` | $3.99 | $10.52 | **$14.51** | $16.50 | $1.21 | 7.3% |
| 14 | **Knit Trio** — plush set of three | `CJWJWJMR00974-Set` | $3.37 | $7.46 | **$10.83** | $12 | $0.52 | 4.4% |
| + | **Fountain Filter Refill** (cotton set) | `CJMY174605312LO` | $2.94 | $5.81 | **$8.75** | $10 | $0.66 | 6.6% |

\* PayPal 2.9% + $0.30 per transaction. **Ad spend is not included, and at these margins there is no
room for it:** every dollar of paid traffic has to come out of the $0.40–$2.80 left on each order.
With a ≤10% ceiling the store is deliberately priced at roughly landed cost — it can win on organic
traffic (Instagram, Pinterest, word of mouth) and on bundles, not on paid acquisition.

**Price history.** 2026-11-27 morning: whole range cut to $49/$59, $49/$54, $24, $15 and a $16 refill
(the "aggressive entry band"). Same day: the user set a **10% net-margin ceiling**, so every price was
recomputed down again to $28/$35, $34/$39, $14/$13, $7 and a $10 refill, and ten new products were
added at the same rule. Any Instagram, Pinterest or email copy made before this second cut still
quotes the old numbers — do not reuse it.

### Watch-outs on the new lines

- **Fish Lick Mat — the $3.00 freight is estimated from the SKU weight (104 g) and the 3-pack rate
  shown on the same listing.** The single-colour SKU sits on the same 104 g body, so freight should
  not differ, but confirm it on the first order.
- **Sisal Scratch Mat ships in the supplier's "Random" colourway (natural oat tones).** Do not promise
  a shade in replies.
- **Carry-Out Cat Bag** has 40,000 factory units; the other cat-carrier candidate
  (`CJJJCWGY02426`, black/blue/grey, $9.67–$12.04) showed **0 US inventory on every size**, which is
  why it was not used.
- **Knit Trio** is the thinnest line in the store (4.4%) because its landed cost is high for a $12
  set; if CJ moves freight again, this is the one to re-price first.
- The **Pulse Tail still ships to US street addresses only (no PO Boxes)** — the rule carries over.

### Sourcing notes — read before changing anything

- **CJ's US warehouse does not stock this category at these price points.** Filtering
  `Ship from: United States` for *dog bed*, *pet bed*, *pet water fountain* and *orthopedic pet bed*
  returned either unrelated US stock (collars, cat trees) or Amazon-style items at $44–$170 that leave
  no margin ($96 "luxury small dog bed", $170 pet sofa). The US-warehouse pet catalog is thin.
- So every SKU above ships **from China via CJ**: processing 1–4 days, delivery 4–9 days for the
  electronics and 5–11 days for the bed, tracked (`CJPacket Sensitive` / `LuWei Ordinary US`).
  That is still one supplier, one dashboard, one card — which is what the store needed — but the site
  no longer claims US-warehouse dispatch or 3–7 day delivery.
- **`CJGY1919307` (the old SteamGroom SKU) is dead** — a SKU search returns no product. It was replaced
  with `CJYD207827101AZ`, the same style of misting/UVC comb (30 ml tank, 3.7 V 300 mAh, three mist
  speeds, UVC on long press).
- **Wipes were removed.** There was no CJ equivalent that cleared $14 retail after freight, so the
  add-on strip now carries only the fountain filter refill.
- Inventory is factory-held (`CJ: 0, Factory: 12 000+`) on every SKU. Nothing is pre-bought, so there
  is no stock risk — but also no head start: a big spike in orders depends on the factory's stock.
- Prices move. Re-check each product page before an ad push; the `landed` values in `CATALOG` are
  documentation, not used by checkout maths.

### What each product actually is (copy must match these)

**1. The Haven Bed — plush cave bed, "crystal velvet", gentleman grey**
- Deep rounded cave, long-pile faux fur outside, plush lining, PP cotton fill; the rim is high enough
  for a cat or small dog to tuck its chin over.
- Sizes 20 in (50 cm) and 26 in (65 cm) across. It is a **cat / small-to-medium dog** bed — not the
  orthopedic memory-foam bed for large breeds the first draft of this page described.
- Do **not** claim machine-washable covers, non-slip bases, foam density or "orthopedic support" —
  none are in the supplier description, which lists only "1 × pet bed".
- Watch-outs: it ships compressed and needs a day to loft; returns are dominated by size, so the size
  guidance in the FAQ matters more than the pictures.

**2. SteamGroom 3-in-1 — mist brush with UVC**
- 30 ml water tank sprays a fine mist ahead of the needles (three speeds), UVC light on a long press,
  head clicks out for cleaning, DC 5 V/1 A charging (~150 min), 3.7 V 300 mAh battery.
- Packing list is **the comb only** — no cable, no charger, no oil. Say "USB charging" only if you
  confirm a cable is included; the listing does not.
- Watch-outs: battery items run 4–8% defect rates; buy a sample and test ten charge cycles before ads.
  Keep "quiet" claims modest.

**3. Stillwater Fountain — 2 L stainless fountain**
- 304 stainless top, clear 2 L tank, ultra-quiet pump, US plug adapter; ships with one filter element
  and two cotton pads. Motion-sense version adds the proximity sensor.
- **Corded, not cordless.** No battery, no 4,000 mAh, no dry-run protection claim — those were in the
  old copy and are gone.
- Repeat purchase: the cotton filter set (`CJMY174605312LO`), sold as the add-on.

---

**4. The Pulse Tail — motion-woken rolling cat ball, "Magic Tail" red**
- A 68 g PC ball on a clear base with a soft silicone tail; it rolls and swings the tail on its own
  and wakes on touch. Three modes (**fast / slow / touch-wake**), an optional bird-chirp sound that
  can be muted, auto-rest after 5 minutes, and it wakes again every 2 hours.
- Works on hard floors and low-pile rugs — **thick carpet stops it**; say so rather than widening the
  claim.
- Built-in battery ("battery contains" on the listing). The supplier does **not** state the charging
  method, so do not write "USB rechargeable" or give a charge time until a sample confirms it.
- **Shipping restriction: US street addresses only — no PO Boxes.** The supplier's listing says the
  carrier cannot deliver this SKU to a PO Box. That restriction is on the product card and in a
  dedicated FAQ entry; keep both if the card is copied elsewhere.
- Only one live variant (Magic Tail red), so the card shows a static `Colour — Magic Tail · red` line
  instead of a one-option `<select>`; `data-add="pulse"` falls back to the first catalog variant.
- Watch-outs: a moving battery toy is the most likely thing in the range to arrive dead or noisy —
  buy a sample, run ten cycles, and keep "quiet" claims modest. Repeat the PO-Box rule in any reply
  to a customer who gives a PO Box address.

**5. Trailhead Harness & Lead — nylon step-in harness with lead**
- Padded nylon, single quick-release buckle, adjustable at chest and neck, metal D-ring between the
  shoulders, lined lead handle. Sold in **L, blue & mustard** (`CJSB217533304DW`), 220 g, box
  300 × 300 × 50 mm.
- The supplier's own listing copy is thin (no reflective claim in the description — the title says
  "reflective", the photos do not show it). **Do not claim reflective stitching** unless a sample
  shows it.

**6. Stillwater Maze Bowl — PP slow feeder**
- Fish-shaped PP bowl with raised ridges and channels, three colours, 170 g, 230 × 230 × 50 mm.
- Sold in green. Food-safe PP per the listing; no dishwasher claim on the page, so none in the store.

**7. Fish Lick Mat — silicone enrichment mat**
- Fish-shaped silicone mat with shallow wavy grooves, three colours, 104 g.
- The listing says "silicone" and nothing about a suction base or freezer use — neither claim is on
  the card.

**8. Tumble Treat — treat-dispensing tumbler**
- Nylon ends + ABS clear centre, 200 g, openings that twist wider or narrower, three sizes
  (96 × 160 × 96 / 120 × 180 × 100 / 300 × 200 × 100 mm). Sold in Large.
- 4,429 lists, 20 reviews, no disputes.

**9. Lure Pod — rechargeable feather teaser + laser**
- ABS, 240 g, 145 × 145 × 92 mm, **USB charging**, replaceable feather wand clipped to a swinging
  arm, laser dot, automatic obstacle avoidance. Two colourways; sold in cherry blossom pink.
- Battery item: buy a sample and check it holds a charge before pushing it in ads.

**10. Sisal Scratch Mat — natural sisal**
- Tight-woven natural sisal on a stitched border, sizes S/M/L/XL, **supplier default colour "Random"
  (natural oat tones)**. Sold in L (706 g).
- Doubles as a wrap: the listing shows it rolled around table and chair legs and fixed there.

**11. Litter Trap Mat — two-layer EVA**
- Honeycomb EVA top that traps litter, waterproof layer underneath, foldable, 339 g.
- Sizes 46 × 60 cm and 55 × 70 cm, black or grey; sold in **grey, 46 × 60 cm, foldable**. The listing
  also sells 2- and 3-packs — those are separate SKUs, not variants of this one.

**12. Carry-Out Cat Bag — soft carrier**
- Oxford cloth shell, nylon mesh on three sides, flat base, zip pocket, webbing handles.
- Sizes S (39 × 17 × 27 cm) and L (44 × 17 × 29 cm), 570 g, grey / light red / blue; sold in
  **blue, L**. 36 reviews.

**13. TrailSip Bottle — 800 ml bottle + trough**
- Food-grade plastic (ABS/HDPE per listing), folding trough, one-press water release with a lock
  button, silicone seal, 210 g, 9 × 9 × 24 cm. Sold in blue-grey.

**14. Knit Trio — three knitted plush squeaky toys**
- Elephant + monkey + poodle, knitted plush with a squeaker in each body, set 226 g (60–94 g each),
  box 280 × 220 × 50 mm.
- **The CJ title still says "squeaky duck"** while the options are elephant, monkey and poodle — the
  store copy was rewritten around the actual animals. Do not copy the CJ title.

## 2. Shipping destinations (measured 2026-11-27)

**Rule in force (user instruction, 2026-11-27):** a country is open only if CJ's freight to it is the
same or lower than CJ's freight to the US for the same SKU — so no order can land above the landed
cost the prices were built on.

**Method.** CJdropshipping live product page → *Ship to* country → the cheapest available method and
the "Shipping Cost" it shows (a DDU customs duty / clearance fee, where the quote adds one, is included).
Quoted at three weights for each candidate country — the lightest line (Pulse Tail, 68 g), a mid line
(Sisal Scratch Mat L, 777 g) and the heaviest/bulkiest (Haven Bed L, 1,402 g). US figures re-confirmed
on the same pages and match the table in §1.

| Country | 68 g — US $5.16 | 777 g — US $14.81 | 1402 g — US $24.86 | Verdict |
|---|---|---|---|---|
| **United Kingdom** | $3.79 | $12.06 | $19.36 | **open** (0.73–0.81 × US) |
| **Canada** | $4.29 | $13.17 | $20.66 | **open** (0.83–0.89 × US) |
| **Japan** | $3.81 | — | $9.47 | **open** |
| **South Korea** | $2.55 | — | $6.40 | **open — except the Haven Bed** |
| **Singapore** | $2.92 | $6.42 | $9.78 | **open** |
| Australia | $5.67 | — | $20.77 | closed — Pulse Tail is above the US quote |
| Germany | $5.73 | — | — | closed — Pulse Tail above US; quote also adds customs duty + clearance |
| France | $6.12 | — | $22.63 | closed — Pulse Tail above US; 12–20 days, customs duty + clearance added |

- **Transit seen on the quotes:** UK 4–9 days (CJPacket Ordinary), Canada 4–15 (JYSP Sensitive / Ordinary),
  Japan 4–5 (Ordinary), Singapore 5–10 (Asia Liquid / Eub), South Korea 8–12 (Eub) but **12–50 days for the
  bed** on the heavy line. US 4–9.
- **Haven Bed blocked in South Korea (user instruction, 2026-11-27).** CJ's cheapest method for the 1,402 g
  Haven Bed to KR (CJPacket Eub) quotes **12–50 days**, so the bed is not sold to South Korea even though the
  country is otherwise open. Implemented in `index.html` as `NOT_IN = { KR: ["bed"] }`: the bed card carries a
  "Ships to US, CA, UK, JP & SG · Not available in South Korea" note, the bag marks the bed line and disables
  *Checkout with PayPal* with an explanatory notice whenever *Deliver to* is South Korea, and the two shipping
  FAQ answers say the same. Every other product still ships to all six countries.
- **Middle weights are interpolated, not individually quoted.** The three measured points per country sit
  in the same narrow band below the US rate, and the site's prices carry 4–9 % net margin, so the band is
  the buffer. Re-quote the exact SKU in CJ before the first order to any new country; the CJ freight tables
  are visible at checkout before payment without placing an order.
- **Customs:** the UK, Canada and Japan quotes show no CJ customs fee line; Singapore quotes carry CJ's DDU
  notice (buyer pays any duty on inspection, <10 % of parcels). Nothing is collected at checkout for duty.
- **Tax registration is not handled:** selling to UK consumers (VAT on consignments ≤ £135) or EU consumers
  (IOSS) creates obligations the store does not yet meet — one reason the EU stays closed. Canada's GST/HST
  registration for non-resident sellers applies above a small threshold. The store is a US-first shop with
  five extra destinations and no tax registration in any of them yet.
- **Checkout guard:** the drawer has a *Deliver to* select listing only these six countries; the chosen
  code is sent to PayPal in the `custom` field ("Ship to CA (Canada)") so the order mail says where it goes.
  PayPal's Cart Upload cannot restrict the buyer's address by itself — the select is a prompt, not a lock.
  Country-level product rules (today: no Haven Bed to KR) are enforced in the drawer by disabling the
  checkout button and refusing to build the form while a blocked line is in the bag — a nudge, not a server
  check, so an order that arrives anyway with a KR address and a bed is a support case, not a bug in PayPal.

## 3. Where to source

| Supplier | Use it for | Notes |
|---|---|---|
| **CJdropshipping** (`CJ6093490`) | **Everything on the store** | One account, one saved card (`mastercard 2526`), tracked shipping, 1–4 day processing. Product pages show live inventory and freight to the US. |
| CJ US warehouse | — | Checked and rejected for these categories (see above). Worth re-checking quarterly — US stock would cut 5–7 days off delivery. |

Rule of thumb: fourteen hero SKUs plus one refill, and **every retail price stays under a 10% net
margin** (0% < margin < 10%, target 4–9%). When CJ moves freight or item price, re-check the landed
cost before anything else: at these margins a $1 freight increase wipes a line out. Cheapest lines to
re-price first are Knit Trio (4.4%), Pulse Tail (5.5%) and SteamGroom white (6.1%).

---

## 4. Operating the store

1. **Order watch** — a scheduled action polls `chaeminleeandrew@gmail.com` for PayPal order mail every
   15 minutes; a real order triggers a fulfilment hand-off.
2. **Fulfilling an order** — PayPal order → cart lines carry the CJ SKU in `item_number` → create the
   order in CJ (`Orders → Store Orders`, or paste the SKU into the cart) → pay with the saved card →
   the tracking number goes back to the customer's PayPal email.
3. **Payment path** — PayPal Cart Upload to `chaeminleeandrew@gmail.com`. Confirm the account can
   receive business payments (a Personal account cannot) with one small live order.
4. **Reviews** — none shown until real orders ship; publish only verified purchases (FTC).
5. **Legal & tax** — real shipping/returns pages, state sales-tax registration, a business entity, and
   only claims that can be substantiated. Delivery estimates on the page (1–4 days dispatch, 4–9 days
   in transit) must stay in line with what CJ actually does.
6. **Publish** — the store lives at `Hearthpaws/hearthpaws.github.io` (GitHub org Pages), served
   straight from `main` → <https://hearthpaws.github.io/>:
   ```
   git add -A && git commit -m "…"
   git push origin main
   ```
   One branch is enough here: for a repo named `<org>.github.io`, Pages publishes `main` /(root) on
   every push. The old address (`chaeminleeandrew-blip/Hearthpaws`) is kept only as a redirect to
   the new one — edit the store here, not there.
7. **Measure** — add analytics (GA4 or Plausible) and a Meta/TikTok pixel before the first ad. Track
   add-to-cart rate (target 8–12%) and checkout start (target 40%+ of carts).

---

## 5. Editing the page

Everything lives in `index.html`.

- **Prices / variants / names / SKUs:** the `CATALOG` object at the top of the `<script>` block. Card
  price markup is static HTML — update both when a price changes.
- **Free-shipping threshold:** `var FREE_SHIP = 50;`
- **Handling fee under $50:** `var SHIP_FEE = 4.95;`
- **Cart storage key:** `hearthpaws-cart-v3` (bump it whenever the SKU list changes, so stale carts
  holding retired items are dropped).
- **Delivery countries:** the `<select id="shipCountry">` in the drawer plus the `SHIPS_TO` map and
  `COUNTRY_KEY` (`hearthpaws-country`). Add a country there and in §2 only after CJ quotes the whole
  range at or below the US rate; the checkout sends the code to PayPal as `custom`.
- **Images:** one 760 × 760 supplier photo per product in `assets/` — `haven-bed`, `steamgroom`,
  `fountain-life`, `pulse-tail` (cards) plus `harness`, `slow-feeder`, `lick-mat`, `treat-tumbler`,
  `lure-teaser`, `scratch-board`, `litter-mat`, `carrier`, `travel-bottle`, `plush-trio`;
  `fountain-product.jpg` is the cart thumb for the fountain. Every one is the supplier's own shot of
  the SKU that ships (see the source URLs in the commit message). Replace, never retouch into a
  different colourway.
- **Colours / type:** CSS custom properties in `:root`.
- **Illustrations:** the hero SVG and the filters cart thumbnail are still inline SVG.

Tested in Chromium at 390 px, 768 px and 1440 px: no console errors, no horizontal overflow, cart
maths correct across variants, quantities, removal, empty state and reload persistence.

Live: <https://hearthpaws.github.io/>
