# TheGame — Ideas & Roadmap

_Running list of what to build next. Add anything anytime; check items off as they ship._
_2D top-down ARPG (Diablo/PoE-like), single file: `game.html`._

## Up next — HIGH priority (in order)
- [ ] **Puzzle for legendary item** — a complex puzzle players must solve to earn a legendary
- [ ] **Hidden rooms** — secret rooms with extra loot to discover

## MEDIUM priority
- [ ] **Rune reroll currency** — from PoE: a currency/item that rerolls an item's stats (or a room's rewards) so you can chase better rolls instead of accepting bad ones. (Harvested from the "Rune reroll currency" chat.)

## Backlog (unordered / low)
- [ ] More character classes (currently 3: Warrior/Hunter/Mage)
- [ ] More spells
- [ ] Custom art / sprites (currently simple shapes)
- [ ] Wrap into desktop app (Tauri/Electron)

## Done
- [x] **Forge (merge items)** — new ⚒ Forge screen (opened from the inventory): stage 3 items of the same rarity into 3 slots, press FORGE, get 1 item of the next rarity up with freshly rolled stats. Result keeps the type of one consumed item. Rarity locks after the first pick; Legendary can't be an input; closing returns staged items. Scrollable list, works on touch + desktop.
- [x] **Cap health potions** — health and mana potions capped at 5 each; when full, flasks stay on the ground (with a toast) instead of being wasted. HUD shows `x/5`.
- [x] **Free-placement touch movement** — floating joystick spawns wherever you touch (no longer locked to the left half); action buttons still take priority. Settings has a Joystick ↔ Tap-to-move toggle, saved across sessions.
- [x] **Scrollable backpack** — inventory now pages through all items (▲/▼ buttons + mouse wheel), with "X–Y of N" indicator and scrollbar. Fixes not being able to see past ~9 items.
- [x] **Difficulty pass** — mobs hit harder & have more HP (steeper per-level scaling); bosses tougher; HP regen SUPPRESSED for 2.5s after taking damage (no free healing mid-fight). Mana regen unchanged.
- [x] **Bigger, touch-friendly inventory** — full two-column panel, large rows, explicit ✕ close button (fixes "character frozen" confusion: game pauses while inventory/settings open; now easy to close on phone).
- [x] **Mobile / touch support** — responsive canvas scaling; virtual joystick (left thumb) for movement; on-screen buttons for attack/spells/potions/inventory/settings; auto-aim at nearest enemy; "rotate to landscape" hint. Desktop controls unchanged.
- [x] **Critical strike** — Crit chance + Crit damage stats (base 5% / 150%); rolls as affix on weapons & jewelry; applies to weapon attacks AND spells; gold floating damage numbers on crit.
- [x] **Settings + rebindable keybinds** — Esc opens Settings; rebind spells/potions/inventory to any key, saved across sessions.
- [x] **Spell levels** — spell tomes level spells (+25% dmg, shorter cooldown); per-class spellbooks on Q/W/E/R
- [x] 3 classes: Warrior / Hunter / Mage, each with own primary stat and spellbook
- [x] Core loop: arrow-keys / click-to-move, weapon attack (melee swing or bow)
- [x] 7 equipment slots, 5 rarity tiers, STR/AGI/INT attributes with derived stats
- [x] Loot drops from enemies/bosses
- [x] Walled rooms, exit door progression, endless scaling levels
- [x] Bosses every 5th level with boosted loot
- [x] Health + mana potions

---
_Ideas parking lot — dump rough thoughts here, sort later:_
- 
