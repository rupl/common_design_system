# Grid

## Purpose and Usage
Basic grid layout with CSS grid and CSS flexbox layout based on @supports queries.

Default grid is 4 columns.

The grid items are no width-restricted so with a 2 column grid, the items will span 50% of the available width.

## Caveats
The selectors must be added to the parent div

### Variants
@TODO better BEM naming for `--2-col` etc
This might be dropped in favour of more robust grid system.

```
.cd-grid-2-col
.cd-grid-3-col
.cd-grid-4-col

```
