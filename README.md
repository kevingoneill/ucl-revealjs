# ucl-revealjs: a University College London slide theme for Quarto

This slide theme was developed to match UCL's [visual branding guidelines](https://www.ucl.ac.uk/brand-and-experience/brand/visual-guidelines).
It includes a custom font, [UCL Sans](https://www.ucl.ac.uk/brand-and-experience/brand/visual-guidelines/typography#font-tag),
as well as an approved [color scheme](https://www.ucl.ac.uk/brand-and-experience/brand/visual-guidelines/colour).

## Installing

```bash
quarto use template kevingoneill/ucl-revealjs
```

This will install the extension and create an example qmd file that you can use as a starting place for your article.

## Using

To use the template format, just include `ucl-revealjs` as the document format:

``` markdown
format:
  ucl-revealjs: default
```

## Format Options

Currently, formatting options are rather limited. Please submit an issue if you have a request.

The main addition is a CSS class `dark`, which can be applied to a slide to display in dark mode:
``` markdown
# Slide title {.dark}

This is a dark slide!
```

## Example

Here is the source code for a minimal sample document: [template.qmd](template.qmd).
