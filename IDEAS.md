# TheGame — Ideas & Roadmap

_Running list of what to build next. Add anything anytime; check items off as they ship._
_2D top-down ARPG (Diablo/PoE-like), single file: `game.html`._

## Up next — HIGH priority (in order)
- [ ] **Armor types per class (cloth / leather / plate)** — each class can only wear its own type:
  - **Mage → Cloth**, **Rogue/Hunter → Leather**, **Warrior → Plate**
  - Armor value: **Cloth < Leather < Plate**
  - Base move speed (no gear): **Rogue fastest → Mage → Warrior slowest**
  - Armor slows you down: **Plate slows most → Leather → Cloth least**
  - Items get an armor-type tag; wrong-type pieces can't be equipped (they become **shard fodder** — nice synergy with the salvage system).
  - *Design watch-outs:* Warrior is both the slowest base AND wears the heaviest armor — the two penalties compound, so plate needs a big enough armor payoff (or a cap on the speed penalty) or he'll feel miserable to play. Also decide whether the speed penalty is flat per piece or scales with the item's armor value.
- [ ] **XP & character levels** — kills grant experience; levelling up raises the character level and **spells scale/level with it** (instead of only via tomes). Open questions to decide: does XP level the character (granting stat points / auto spell ranks), or feed each spell separately? Suggested: character level → +primary stat and +1 spell rank every N levels; XP bar in the HUD; enemies grant XP scaled by region/cycle.
- [ ] **Auras (passive spells)** — collectable passives, **max 4 equipped** (swappable). Dropped by region bosses / rare relics; level up like spell tomes (stacking effect per level). Proposed pool:
  - **Precision** — +Crit chance
  - **Brutality** — +Crit damage
  - **Concussive Blows (Bash)** — chance on hit to stun briefly *(needs an internal cooldown or diminishing returns, otherwise it perma-locks packs)*
  - **Alacrity** — +attack speed and +spell haste
  - **Bloodthirst (leech)** — heal for a % of damage dealt *(scales dangerously with big hits — cap it per hit)*
  - **Thorns** — reflect damage back to attackers
  - **Frost Aura** — enemies near you are permanently slowed (great in Verdant Hollow swarms)
  - **Immolation** — constant AoE burn around you *(strong vs swarms; keep the damage low)*
  - **Fortitude** — +max HP and +Armor
  - **Clarity** — +mana regen and cheaper spells
  - **Executioner** — bonus damage to enemies below 25% HP
  - **Momentum** — move speed spikes after each kill
  - **Chain Reaction** — kills have a chance to explode, damaging nearby enemies
  - UI: 4 aura slots shown in the HUD, managed from the inventory; auras are passive (no key needed).
- [ ] **Puzzle for legendary item** — a complex puzzle players must solve to earn a legendary
- [ ] **Hidden rooms** — secret rooms with extra loot to discover

## MEDIUM priority
- [ ] **Rune reroll currency** — from PoE: a currency/item that rerolls an item's stats (or a room's rewards) so you can chase better rolls instead of accepting bad ones. (Harvested from the "Rune reroll currency" chat.)

## Backlog (unordered / low)
- [ ] More character classes (currently 3: Warrior/Hunter/Mage)
- [ ] More spells
- [ ] Custom art / sprites (currently simple shapes)
- [ ] Wrap into desktop app (Tauri/Electron)
- [ ] **Sound** — SFX for hits, crits, spells, loot pickup, level up, boss spawn, forge; maybe background music. Needs a mute toggle in Settings.

## Done
- [x] **Character sheet + item coherence** — the inventory now shows a live **Character** panel (all primaries + Attack Dmg, Attack Speed, Crit, Crit Dmg, Spell Power, Spell Haste, Armor, Move Speed, Max HP/Mana) that updates as you swap gear. Item generation is now **coherent**: an INT weapon is a caster weapon granting Spell Power — never Attack Damage — so combos like "Staff: +Attack Dmg +INT" can't happen. Verified across 3000 generated items.
- [x] **Weapon variants + Attack Speed + cooldown rebalance** — weapons roll one of several PRIMARY stats so a type can suit several classes (Dagger = AGI/AtkSpeed/Crit **or** INT/Crit/CritDmg; Sword = STR or AGI; Mace = STR or INT), with secondaries drawn from a pool matching that primary, and a 3rd stat line on higher rarities. New **Attack Speed** secondary. Big AoE spells rebalanced to long cooldowns with far higher damage (Meteor 6s/300, Heroic Leap 5s/230, Arrow Rain 4s/150) while spammables stay fast; Spell Haste (= cooldown reduction) makes those nukes a real build choice. Spell bar now shows cooldowns in seconds.
- [x] **Regions / biomes** — 4 themed regions of 5 levels each ending in a boss: **Frostvale** (tanky, slow), **Verdant Hollow** (fast swarms), **Emberwaste** (hits hardest), **Shadowmire** (fast + mean). Each has its own palette, walls, enemy colours and scenery props, plus an entry banner. After Shadowmire the cycle repeats as **Cycle 2, 3…** with a big difficulty ramp (×1.85 per cycle) so late-game gear stops one-shotting. Story/lore to be written later.
- [x] **Shards (salvage & craft)** — destroy unwanted loot for 1 shard of its rarity (Inventory → ✖ Salvage, with bulk "salvage all Normal/Uncommon/Rare"). **10 shards of a rarity = craft ANY item type of that rarity** with random stats (Forge → ✦ Shards tab). Junk flows upward via **3 lower shards → 1 higher shard**. Costs are constants (SHARD_COST / SHARD_CONVERT) so they're easy to tune.
- [x] **WoW-style stat rework** — STR/AGI/INT are PRIMARY (gold in UI); Armor, Speed, Crit, Crit Dmg, Spell Power, Spell Haste are SECONDARY (grey). Staff/Wand are caster weapons granting **Spell Power instead of Attack Damage** (spell damage now scales with it). New 1H **Dagger** (fast, AGI) and Sword pair with off-hands; new caster off-hands **Tome** (INT) and **Orb** (Spell Power), alongside Shield. New rollable **Spell Haste** cuts spell cooldowns.
- [x] **Portrait mode on mobile** — playfield switches between portrait (560×900) and landscape (900×560) automatically on rotate; no more "rotate your phone" nag. Buttons anchored to screen edges; class menu stacks vertically; inventory & forge use a single column in portrait.
- [x] **Two-handed weapons block shields** — new 1H/2H split: 1H Sword/Axe/Mace can pair with an Off-hand shield; 2H Greatsword/Battle Axe/Warhammer/Staff/Bow hit harder but auto-unequip the shield (and vice versa), with a toast. Off-hand slot shows "blocked", items tagged "· 2H".
- [x] **Forge (merge items)** — new ⚒ Forge screen (opened from the inventory): stage 3 items of the SAME TYPE **and** rarity (e.g. 3 Uncommon Bows), press FORGE, get 1 of that same type one rarity up (Rare Bow) with freshly rolled stats. Type+rarity lock after the first pick and non-matching items dim; list is grouped so sets are easy to find. Legendary can't be an input; closing returns staged items. Works on touch + desktop.
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
