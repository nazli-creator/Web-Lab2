# Web-Lab2

Single-page website that shows two different appearances (Style A and Style B) depending on which stylesheet the HTML links to. Built with only HTML and CSS, as required by the assignment.

## File Organization

```
Web-Lab2/
├── index.html    # Page structure: a .container div holding six .box elements (A-F)
├── styleA.css    # Layout A: boxes stacked vertically, evenly spaced
├── styleB.css    # Layout B: boxes placed side by side, last one pinned to a corner
└── README.md     # This file
```

## Challenges I Faced

- **Keeping the boxes evenly spaced without resizing them (Layout A):** using margins for spacing would have needed manual recalculation on resize. Solved by fixing the box `width`/`height` and letting the flex container's `justify-content: space-evenly` absorb the extra space instead.
- **Centering the text in the last box:** `text-align: center` only centers text horizontally. To center it vertically as well, I turned that box into a flex container with `align-items: center` and `justify-content: center`.
- **Keeping the boxes on one line in Layout B:** the boxes wrapped to a new line on narrow screens, so I added `flex-wrap: nowrap` to the container.
- **Pinning the last box to a corner independent of the others:** `position: fixed` was needed so the sixth box stays anchored to the viewport corner regardless of window size, while still being defined as a normal child in the same HTML structure as the other boxes.
- **Reusing one HTML file for two very different layouts:** since only CSS may differ between versions, all layout logic (alternating colors, spacing, positioning) had to be expressible purely through selectors like `:nth-child` and class names, without changing the markup.
