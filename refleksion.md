# Min side

Overordnet set blev det til lidt af en rodebutik.

### CSS

CSS'en er organiseret i et hierarki med Cascade layers i main.css:

```
@import url("./reset.css") layer(reset);
@import url("./global.css") layer(global);
@import url("./overrides.css") layer(overrides);
```

Den globale CSS er naturligvis den der bliver brugt mest på siden, med `:root`, hvor jeg har lavet spacing
`--step--2`og typografi, samt farver.

## Hvad gik godt?

## Hvad gik mindre godt?
