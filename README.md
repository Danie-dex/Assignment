1. Why did you choose Grid for the recipe cards and Flexbox for the About section? What would break if you swapped them?

    Grid is designed for two-dimensional structures, making it the perfect tool to map cards evenly across both columns and clean, standardized rows. Flexbox works ideally in one dimension, allowing the text stack and image container in the "About" section to easily scale alongside each other without strict, forced track dimensions. If swapped, mapping cards in Flexbox would require using precise calculated percentage widths on wrapping flex items (which easily break alignment if card text amounts differ). Meanwhile, using Grid for the About section would complicate simple centering constraints and force us to declare arbitrary column sizes instead of letting the content shift and flow natively.

    2. What was the hardest part of making the layout responsive? How did you solve it?

    The hardest part was ensuring that uneven content in our recipe cards (different length descriptions) did not warp or stretch individual cards differently when changing viewport widths. I solved this by treating the card wrapper as a nested flex column structure (flex-direction: column) and assigning flex-grow: 1 specifically to the description paragraphs. This design dynamic forces all card elements to stretch identically down to the structural card bottoms, providing crisp, aligned margins across the entire row grid.

    3. Where did you use a CSS variable, and why was that better than hardcoding the value?

    I used CSS variables for structural design variables like colors (--primary, --background) and timing (--transition-speed). This was immensely superior to hardcoding values because it allowed me to instantly construct a Dark Mode feature by simply redefining the properties nested inside a single @media (prefers-color-scheme: dark) media block. Had I hardcoded hex colors, I would have been forced to manually redefine properties across dozens of isolated target classes and tags throughout the entire CSS file.

    4. If you added one more recipe card (a 4th), what would you need to change in your CSS, and why?

    Under the current layout, adding a fourth card would either squish the cards into four narrow columns (which compromises readability on smaller laptops) or force the fourth card to isolate itself on a new line beneath. To solve this smoothly, I would change the grid-template-columns template property from repeat(3, 1fr) to repeat(auto-fit, minmax(300px, 1fr)). This change bypasses explicit columns entirely, directing the grid engine to dynamically fit as many cards as physically possible onto a row, wrapping any additional cards (like a 4th) cleanly to the next row once columns run out of room.