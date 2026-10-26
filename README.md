# ucl-revealjs: a University College London slide theme for Quarto

This slide theme was developed to match UCL's [visual branding guidelines](https://www.ucl.ac.uk/brand-and-experience/brand/visual-guidelines).
It includes a custom font, [UCL Sans](https://www.ucl.ac.uk/brand-and-experience/brand/visual-guidelines/typography#font-tag),
as well as an approved [color scheme](https://www.ucl.ac.uk/brand-and-experience/brand/visual-guidelines/colour).

**This template is made only for official use by students, staff, and faculty of University College London.**

## Installing

```bash
quarto use template kevingoneill/ucl-revealjs
```

This will install the extension and create an example qmd file that you can use as a starting place for your article.

## Using

To use the template format, just include `ucl-revealjs` as the document format:

```markdown
format:
  ucl-revealjs: default
```

## Format Options

### Dark mode
```markdown
# Slide title {.dark}

This is a dark slide!
```

### Font sizes

There are a number of CSS classes available for font sizing:

```markdown
[Extra tiny]{.extra-tiny}
[Tiny]{.tiny}
[Much smaller]{.much-smaller}
[Smaller]{.smaller}
[Regular]{}
[Larger]{.larger}
[Much larger]{.much-larger}
[Huge]{.huge}
```

### Positioning
And for positioning:

```markdown
[Left]{.left}
[Right]{.right}
[Top]{.top}
[Bottom]{.bottom}
[Top Left]{.top-left}
[Top Right]{.top-right}
[Bottom Left]{.bottom-left}
[Bottom Right]{.bottom-right}
[Center]{.center-xy}
[Center Horizontally]{.center-horizontally}
[Center Vertically]{.center-vertically}
```

### FontAwesome Icons

```markdown
[<i class="fa-solid fa-face-smile"></i>]{.huge}
```

### Boxes

```markdown
:::{.columns}
::::{.column .box width="40%"}
- This is a boxed column
- With some content
::::

::::{.column width="5%"}
::::

::::{.column .box width="40%" .fragment}
- This is a another boxed column
- With some more content
::::
:::
```

### Plotting utilities

The file `_assets/plotting.R` defines all colors approved by the UCL branding guidelines for use in `R`, as well as a theme `theme_ucl()`. It also contains the function `hide_plot`, which allows one to animate sub-panels of a multi-panel figure:

```markdown
:::{.r-stack}
::::{.fragment}
````{r}
#| label: plot2-1
#| fig-width: 10
#| fig-height: 4
(plot1 + hide_plot(plot1)) +
  plot_layout(guides="collect")
````
::::

::::{.fragment}
````{r}
#| label: plot2-2
#| fig-width: 10
#| fig-height: 4
(plot1 + plot1) +
  plot_layout(guides="collect")
````
::::
:::
```

### TikZ Figures

The file `_assets/tikz_header.tex` includes TikZ styling for use in diagrams. I recommmend combining this with [the `quarto_tikz` extension](https://github.com/danmackinlay/quarto_tikz):

`svg-command: "pdf2svg {input} {output}"  # use pdf2svg because inkscape breaks fonts`

```markdown
:::{.r-stack height=600}
::::{.fragment .center-flex}
````{.tikz width=1000}
%%| filename: binary_causal_structure_1
%%| additionalPackages: \usepackage{amsmath}
\include{_assets/tikz_header.tex}
\begin{tikzpicture}[-Latex]
	\node[state, hidden] (E) {$E$};
    \node[state] (C) [above left = of E] {$C$};
    \node[state, hidden] (A) [below left = of E] {$A$};
    \path[hidden] (C) edge (E);
    \path[hidden] (A) edge (E);
    \node[unboxed, minimum size=0cm, hidden] (eqnA) [right = 1cm of E] {$A \sim \bernoulli{p_A}$};
    \node[unboxed, minimum size=0cm] (eqnC) [above = .5mm of eqnA] {$C \sim \bernoulli{p_C}$};
    \node[unboxed, minimum size=0cm, hidden] (eqnE) [below = .5mm of eqnA] {$E = \; C \wedge A$};
\end{tikzpicture}
````
::::

::::{.fragment .center-flex}
````{.tikz width=1000}
%%| filename: binary_causal_structure_2
%%| additionalPackages: \usepackage{amsmath}
\include{_assets/tikz_header.tex}
\begin{tikzpicture}[-Latex]
	\node[state, hidden] (E) {$E$};
    \node[state] (C) [above left = of E] {$C$};
    \node[state] (A) [below left = of E] {$A$};
    \path[hidden] (C) edge (E);
    \path[hidden] (A) edge (E);
    \node[unboxed, minimum size=0cm] (eqnA) [right = 1cm of E] {$A \sim \bernoulli{p_A}$};
    \node[unboxed, minimum size=0cm] (eqnC) [above = .5mm of eqnA] {$C \sim \bernoulli{p_C}$};
    \node[unboxed, minimum size=0cm, hidden] (eqnE) [below = .5mm of eqnA] {$E = \; C \wedge A$};
\end{tikzpicture}
````
::::

::::{.fragment .center-flex}
````{.tikz width=1000}
%%| filename: binary_causal_structure_3
%%| additionalPackages: \usepackage{amsmath}
\include{_assets/tikz_header.tex}
\begin{tikzpicture}[-Latex]
	\node[state] (E) {$E$};
    \node[state] (C) [above left = of E] {$C$};
    \node[state] (A) [below left = of E] {$A$};
    \path (C) edge (E);
    \path (A) edge (E);
    \node[unboxed, minimum size=0cm] (eqnA) [right = 1cm of E] {$A \sim \bernoulli{p_A}$};
    \node[unboxed, minimum size=0cm] (eqnC) [above = .5mm of eqnA] {$C \sim \bernoulli{p_C}$};
    \node[unboxed, minimum size=0cm] (eqnE) [below = .5mm of eqnA] {$E = \; C \wedge A$};
\end{tikzpicture}
````
::::
:::
```


## Example

Here is the source code for a minimal sample document: [template.qmd](template.qmd).
