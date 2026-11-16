# Staking — Phase 1 prototype

An interactive prototype of the tournament staking feature, scoped to **Phase 1 of
Staking — Draft 1**. It is a single self-contained HTML file: open `index.html` in a
browser, no build step and no dependencies beyond a web font.

## What it covers

Built on a CoinPoker-style lobby skeleton, with staking added as a tab in the
player panel.

**Backer**
- Staking list with Bought / Seller / Markup / Available, search and an
  available-only filter
- Two-phase component: **1 · Profile** (PokerIntel stats, staking history, the
  seller's note, the offer terms, sold progress) → **2 · Buy Action** (share
  slider, live cost, payment, confirm)
- Cost is `buy-in × share × markup`, never entered by hand
- Share sells in GG's fixed increments, derived from the buy-in: 10% below 26,
  1% up to 5,000, 0.1% above
- Per-backer cap enforced against the share already held
- Payment in USDT or T$, each with its own balance check
- Stakes are final once confirmed

**Seller** — `Sell Action` in the lobby header
- Share to sell, capped by the back-office maximum
- Markup within the back-office range
- Optional per-backer cap
- Optional auto-unregister if the action does not sell by the start
- Personal note (140 characters)
- Live view of face value, markup premium, what backers pay and the seller's net
  cost
- Once listed: Cancel Sell Action / Sell More

**Operator limits** are applied in code (`BO`), not exposed as a screen.

## Deliberately out of scope

Present in the GGPoker reference, absent from Draft 1: share dilution for
re-entries, designating specific backers, automatic settlement of winnings,
staking chat and follow, selling after the start or on Day 2, and timed entry.

## Open questions the prototype assumes an answer to

Draft 1 leaves these to product. The prototype picks an answer so the flow is
complete; each is cheap to change.

| Question | Assumed |
| --- | --- |
| Does the per-user cap apply per entry or per tournament? | Per entry |
| Can one backer buy twice from the same seller? | Yes, stacking against the same cap |
| When does the seller receive the backer's money? | Held until the tournament starts |
| Which ticket types can be staked? | Cash entries only |

Data in the file is sample data. Nothing here is production code.
