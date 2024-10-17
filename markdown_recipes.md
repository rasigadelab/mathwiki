## Markdown recipes

The following is a description of the operations performed to transform a ChatGPT-generated math document into a proper Github document. Attention is given to the proper display of formulae, esp. matrices.

- inline math: replace `\( ` and `\)` with `$` everywhere, removing leading and trailing spaces
- display math: replace `\(\n` and `\n\)` with `$$` (double dollars). Remove any space or line break inside the math environment. Remove any space before the opening `$$`. Insert line breaks above and below the display math formula.
- inline and display math: LateX parsing fails in Github markdown if two `*` are encountered. Avoid accents such as $x^*$, use other signs, e.g., $x^+$
- check that all `\\` line breaks are followed with a line break (LateX does not enforce this, Github markdown does)

## Useful resources

- printing ChatGPT conversations (including math) to PDF: https://blackravenlabs.com/