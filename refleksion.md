# Min side

Dette var et større projekt, hvor jeg forsøgte mig at gøre brug af teknikker vi har arbejdet med i undervisningen.
Det var en blandet pose af resultater, hvor nogle ting lykkedes og andre ting mislykkedes. Det blev derfor til et projekt baseret på kompromis, fremfor perfektion.

### CSS

CSS'en er organiseret i et hierarki med Cascade layers i main.css:

```css
@import url("./reset.css") layer(reset);
@import url("./global.css") layer(global);
@import url("./overrides.css") layer(overrides);
```

``@layer reset, global, components, overrides; `

Den globale CSS er naturligvis den der bliver brugt mest på siden, med `:root`, hvor jeg har lavet spacing
` --space-3xs:`
og typografi `--step--2`, samt farver `--yellow: #ffcc4a;`.

## Hvad gik godt?

Jeg forsøgte at bruge **selectors** hvor det gav mening, og lagde størstedelen af min energi i at prøve at implementere dem samtlige steder på siden.

Et par udpluk fra siden af hvad der lykkedes:

Eksempel på at "kalde" på et bestemt child i min section/div:

```css
.text :first-child {
  margin-bottom: var(--space-l);
}
.text :nth-child(2) {
  margin-bottom: var(--space-l);
}
```

"Kalder" på article inde i min section

````css
section > article {
display: grid;
grid-template-columns: 1fr 1fr;
background-color: var(--bg-black);
height: auto;
}```

Derudover benyttede jeg mig af **pseudo-elementer**, `::before` og `::after`. De bliver egentlig brugt til at generere ekstra indhold før og efter elementets egentlige indhold. Derudover har jeg nestet dem, så de ligger direkte inde i min parent selector, i dette tilfælde `.stat`.
```css
.stat {
container: stat / inline-size;
--actualPercent: calc(var(--percent) _ 1%);
--border-width: 5px;
aspect-ratio: 1;
width: 150px;
border-radius: calc(infinity _ 1px);
border: var(--border-width) solid transparent;
background:
conic-gradient(var(--yellow) 0 0) padding-box,
conic-gradient(white var(--actualPercent), var(--p-grey) 0) border-box;
font-weight: bolder;
display: grid;
counter-reset: c var(--percent);
&::before,
&::after {
grid-area: 1 / 1;
}

    &::after {
      content: counter(c, decimal-leading-zero) "%";
      place-self: center;
      font-size: 30cqw;
      font-variant-numeric: tabular-nums;
    }

    &::before {
      content: "";
      aspect-ratio: 1;
      border-radius: 99px;
      width: 20px;
      offset-path: border-box;
      offset-distance: var(--actualPercent);
      background: var(--bg-black);
      offset-anchor: 50% calc(50% - var(--border-width) / 2);
    }

}

## Hvad gik mindre godt?

I stedet for at bruge **Container queries** har jeg mest benyttet mig at **Media queries**. Hvis jeg havde brugt container queries havde jeg haft den fordel, at mit indhold havde tilpasset sig efter hvor meget plads der er til containerne, fremfor hvor meget plads der er i viewporten. Jeg havde til gengæld svært ved at forstå det, og da jeg i forvejen var frustreret over at koden som resultat drillede hist og her, valgte jeg at droppe det. Hvis ikke der var deadline på, havde jeg formegentlig lagt mere energi i det, fremfor at prioritere hvad jeg kunne forstå, og hvad der i forvejen fungerede for mig.

Ydermere forsøgte jeg mig med **subgrid**, men det gav blandede resultater for mig, og igen med henblik på hvad der fungerede, tog jeg et skridt tilbage og fortsatte med hvad der gav mening for mig.

````
