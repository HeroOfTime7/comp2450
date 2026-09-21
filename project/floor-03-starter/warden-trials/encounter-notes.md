# Trial III — *The Encounter* — Notes

*Warden of the Foundations · Midterm 1 · 60 %*

This file is the grader's map of your battle code. Help us find each piece. Be specific — file and line numbers are encouraged.

---

## AI declaration for Trial III

Did not use

---

## Two functions I wrote without AI assistance

These are the functions Friday's quiz can ask me to modify on paper. I wrote each of these by hand, with no autocomplete on the body. Pick functions you know cold — three of the four quiz questions pull from these.

1. `<useBattleMenu>` in `<Battle.cpp>:<135>`
2. `<wardenFights>` in `<Battle.cpp>:<95>`

---

## Floor 0–3 ties — where to find them in my code

Help the grader find each of the four required ties.

**Floor 0 (ADT).** The available menu actions are stored in:

- Container type: `<enum>`
- Declared at: `battle/Battle.cpp:<88>`
- BattleMenuOptions, I used this to easily store selected inputs.

**Floor 1 (search).** `findByName<Item>` is called at:

- `battle/Battle.cpp:<125>` (Use-item branch)

**Floor 2 (sort).** The at-display sort (`std::sort` with a comparator, or your Floor 2 `sortInventory`) is called at:

- `battle/Battle.cpp:<119>` (before displaying the items menu)
- Sort criterion: `<value asc>` (e.g., descending value — the healing-power stand-in — or ascending weight)
- I thought it would be the most helpful when trying to find the most potent item.

**Floor 3 (templates + exceptions).** `BattleException` (or `BagException` where a bad index is the fault) is:

- Thrown at: `battle/Battle.cpp:<164>` on `<invalid input>`
- Caught at: `battle/Battle.cpp:<null>` no catch, just continues in the loop.

---

## Reflection  *( ≤ 200 words )*

The hardest was ADT because I didn't really need an enum. I forgot to include that part of the project and instead just wired my inputs straight into if/else statements. Both work, but I must say the enums are nice to look at.

---

## Tuning notes (optional)

If you changed any of the tunables (`kPlayerStartHP`, `kWardenStartHP`, `kPlayerAttackDmg`, `kWardenAttackDmg`), or added new ones (item healing amounts, etc.), list them and their values here so the grader can play through your battle without surprise.

(your notes, or "defaults")
