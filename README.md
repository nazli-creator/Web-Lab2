# Web-Lab2

Single-page website that shows two different appearances (Style A and Style B) depending on which stylesheet the HTML links to. Built with only HTML and CSS, as required by the assignment.

## File Organization

- `index.html` — the single HTML document shared by both versions. Contains one `.container` wrapping six `.box` elements (`A`–`F`). The sixth box has an extra `.last` class since it is styled differently from the rest in both versions. By default it links to `styleA.css`.
- `styleA.css` — "Version A": boxes stacked vertically, centered horizontally, evenly spaced with flexbox (`justify-content: space-evenly`) so spacing adjusts on resize while box size stays fixed. Boxes alternate background colors via `:nth-child`, and the last box gets a distinct background and a 4px black border.
- `styleB.css` — "Version B": the first five boxes sit in a row in the top-left corner (`display: flex; flex-wrap: nowrap` so they never wrap), and the last box is pinned to the bottom-right corner with `position: fixed`. All boxes get a hover effect that changes the cursor and swaps the background/text colors.

To switch between versions, change the `href` of the `<link>` tag in `index.html` between `styleA.css` and `styleB.css`.

## Challenges Faced

- **Keeping spacing dynamic without resizing the boxes (Style A):** using `height`/`width` on the boxes for spacing would have changed their size on resize. Solved by fixing the box dimensions and letting the flex container's `justify-content: space-evenly` absorb the extra space instead.
- **Preventing the boxes from wrapping on narrow windows (Style B):** the default flex behavior wraps items when space runs out. Setting `flex-wrap: nowrap` on the container keeps all boxes on one line, letting the layout overflow horizontally instead of wrapping.
- **Pinning the last box to a corner independent of the others:** `position: fixed` was needed so the sixth box stays anchored to the viewport corner regardless of window size, while still being defined as a normal child in the same HTML structure as the other boxes.
- **Reusing one HTML file for two very different layouts:** since only CSS may differ between versions, all layout logic (alternating colors, spacing, positioning) had to be expressible purely through selectors like `:nth-child` and class names, without changing the markup.
