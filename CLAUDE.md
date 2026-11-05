# Global instructions

## Math formatting

Always write mathematical formulas in LaTeX in your responses: use `$...$` for inline math and `$$...$$` for display equations. Do not use plain-text or Unicode approximations (e.g. write `$x^2 + y^2 = r^2$`, not `x^2 + y^2 = r^2` or `x² + y² = r²`).

Never wrap a bare number in math delimiters: the renderer treats `$` followed by a digit as a currency sign and breaks the surrounding formulas. Write plain numbers as plain text (0.90, not `$0.90$`). If a number belongs to a formula, put it inside a full expression that starts with a symbol (e.g. `$p_1 = 0.90$`, `$\text{IoU} = 0.5$`).

## Graphs and schemas

Whenever you create a graph, diagram or schema (flowcharts, architectures, state machines, sequence diagrams, dependency graphs, pipelines, etc.), use Mermaid if it has suitable tooling for that diagram, unless the user specifies another format. Pick the output as follows:

- **Default: a fenced ```` ```mermaid ```` block.** The Claude desktop app renders these with HTML labels off, so `$$...$$` in a label shows up as literal text. Never put LaTeX in these blocks.
- **When the diagram needs, or would clearly benefit from, math formulas in its labels: a Mermaid widget**, rendered with `mcp__visualize__show_widget` if that tool is available. Use it only in that case, because a widget can't be copied as a Mermaid block and has to download Mermaid when it loads. Math only works in flowcharts and sequence diagrams.
- **If no widget tool is available:** use a fenced block with plain-text labels (e.g. `input x`) and define the symbols in LaTeX in the text around the diagram.

In a Mermaid widget:

- Load Mermaid with `import mermaid from 'https://esm.sh/mermaid@11.17.2/dist/mermaid.esm.min.mjs'`, and add `<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.47/dist/katex.min.css">` plus `<style>.katex-display{margin:0}</style>`.
- Call `mermaid.initialize` with `htmlLabels: true`, `flowchart: { htmlLabels: true }` and `forceLegacyMathML: true`. Without `forceLegacyMathML`, `\mathbf` and `\mathcal` lose their styling.
- Write the diagram source in `` String.raw`...` `` so backslashes survive.
- Quote labels that contain math, and keep each formula on one line, using only KaTeX-supported commands.
- Add `\;` inside the formula on any side that touches text, because spaces outside `$$...$$` are dropped: `"input $$\;\mathbf{x}$$"`, `"$$\mathbf{y}\;$$ passed on"`, `"a $$\;x\;$$ b"`.
