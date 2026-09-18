# Trial I — *The Foundations Brief*

*Warden of the Foundations · Midterm 1 · 15 %*

Four short answers, one from each floor above. **50–100 words per answer.** No code on this trial (except the lambdas in Q3); just clear thinking.

AI is welcome to *check* your answers; it is not welcome to *write your sentences*. These answers are short enough that an LLM voice is recognisable.

---

## 1. Floor 0 — ADT

> Your battle's "Use item" menu shows the *currently usable* items in your hero's inventory on this turn. Name the right ADT for that menu. Defend the choice against its closest neighbour (e.g., why `bag` instead of `set`, or `list` instead of `bag`).

A bag would be the best choice for an inventory system. Compared to a set, a bag can hold duplicates of items, allowing you to carry multiple swords and health potions. The bag closely represents a physical bag as well because of it being unordered. It is very easy for us to print out all the items from a bag as well.

---

## 2. Floor 1 — search & Big-O

> Your inventory is kept sorted by healing power (in this codebase an item's `value` measures its potency, so `value` plays the healing-power role). The player types `use Healing potion`. Linear or binary search to find it by name? Justify, and give the Big-O for each.

Binary search is considerably faster than linear search and would be the best method to find an item. This of course only works if it is sorted, but when talking about the potency of the items it only makes sense since they are sorted by value. Binary search should be able to find it much faster in this situation.

---

## 3. Floor 2 — sort & comparators

> Your "Use item" menu must be displayable sorted *either* by healing power (meaning `value`) *or* by weight. Show a one-line comparator (lambda) for each. One sentence on what language feature makes one `std::sort` call serve both orders.

*Note: `Item` has no healing field — an item's `value` measures its potency, so `value` plays the healing-power role here and in your battle.*

```cpp
// by healing power — i.e. by value
auto byValue  = [](const Item& a, const Item& b) {return a.value < b.value};

// by weight
auto byWeight = [](const Item& a, const Item& b) {return a.weight < b.weight};
```

It would be an annonymous function.

---

## 4. Floor 3 — templates & exceptions

> Why does `Bag<T>` live in `Bag.h` instead of `Bag.cpp`? And: when the player types `9` for a 4-option menu, where in your code should the validation **throw**, and where should it **catch**?

The template for Bag lives in the Bag header file because the header file acts like a blueprint for the Bag.cpp file. All implementation would be applied in the cpp file, but since the template lays out how the template should operate, then it belongs in the header file. It should throw a BagException when using .at and should print it from the BagException.h file.
