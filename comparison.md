# Flexbox vs. CSS Grid — Comparison

Both `flexbox.html` and `grid.html` render the identical pricing section. Building it twice made the tradeoffs concrete rather than theoretical.

## Which one was easier for this pricing layout?

**Flexbox was easier for the base case, but Grid made the responsive re-ordering cleaner.**

For a simple "3 equal cards in a row that wrap on small screens," Flexbox took less code: `display: flex; flex-wrap: wrap; justify-content: center; gap: 2rem;` on the container plus a `flex-basis` on each card was enough to get a working, responsive row. Grid needed one extra concept up front — naming each card's grid area — but that setup paid off at the tablet breakpoint, where Enterprise needed to visually span a full row below Basic and Pro. In Grid, that's a two-line change to `grid-template-areas`. In Flexbox, the equivalent relies purely on source order and `flex-wrap`, with no extra property needed at all — which is arguably even simpler, as long as the order you want on screen matches the order in the HTML. (An earlier draft used Flexbox's `order` property to reshuffle the Pro card on tablet — it was removed so both versions demonstrate the same visual result from the same source order, keeping the comparison focused on layout method rather than manual reordering.)

## When Flexbox is better

- **One-dimensional layouts** — a single row or column of items, like this card row, a navbar, or a button group.
- **Content-driven sizing** — when you want items to size themselves based on their content and share leftover space (`flex-grow`/`flex-shrink`).
- **Simple, predictable wrapping** — `flex-wrap` combined with `flex-basis` is a fast way to get "as many as fit per row" behavior.
- **Alignment-heavy UI** — centering a single item, distributing icons/buttons evenly, vertically centering content in a card.

## When Grid is better

- **Two-dimensional layouts** — anything that needs to control rows *and* columns at once, like this pricing section combined with its header/footer, a dashboard, or a photo gallery.
- **Explicit structural placement** — `grid-template-areas` lets you name regions ("basic", "pro", "enterprise") and rearrange them per breakpoint without changing the HTML order or reaching for `order`.
- **Overlapping or precise spans** — a card that should span two columns, or elements that intentionally overlap, are far more natural in Grid.
- **Layouts defined "top-down"** — when you know the shape of the layout first (e.g., "2 columns, second row spans full width") and want to declare it directly, rather than building it up item-by-item.

## Advantages & disadvantages

### Flexbox

**Advantages**
- Less code for simple rows/columns
- Great content-based sizing and space distribution
- Very predictable wrapping behavior with `flex-wrap`
- Slightly wider legacy browser support

**Disadvantages**
- Only one axis at a time — reordering across both rows and columns needs `order` tricks
- Wrapping items don't automatically align into clean columns across rows (no built-in row/column tracks)
- Precise placement (e.g., "put this in row 2, column 1") isn't a first-class feature

### CSS Grid

**Advantages**
- True two-dimensional control over rows and columns
- `grid-template-areas` gives readable, self-documenting layout structure
- Effortless visual reordering per breakpoint without touching HTML or using `order`
- Handles complex, asymmetric layouts (spans, overlaps) naturally

**Disadvantages**
- Slightly steeper learning curve (template areas, track sizing, implicit vs explicit grids)
- Can feel like overkill for simple single-row/column components
- A little more upfront planning needed to name areas and columns correctly

## Takeaway

For **this specific pricing section**, both approaches produced the same visual result and neither was "wrong." Flexbox was faster to reach for and reads simply for a single row of cards. Grid required a touch more setup but made the tablet/mobile re-ordering more declarative and easier to reason about. In practice, many production UIs use **both together** — Grid for the page/section-level structure, Flexbox for the smaller components inside each grid cell (which is exactly what this project's card internals — icon + text rows in the feature list — already do).
