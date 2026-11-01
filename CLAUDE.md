# Global instructions

## Math formatting

Always write mathematical formulas in LaTeX in your responses: use `$...$` for inline math and `$$...$$` for display equations. Do not use plain-text or Unicode approximations (e.g. write `$x^2 + y^2 = r^2$`, not `x^2 + y^2 = r^2` or `x² + y² = r²`).

Never wrap a bare number in math delimiters: the renderer treats `$` followed by a digit as a currency sign and breaks the surrounding formulas. Write plain numbers as plain text (0.90, not `$0.90$`). If a number belongs to a formula, put it inside a full expression that starts with a symbol (e.g. `$p_1 = 0.90$`, `$\text{IoU} = 0.5$`).

## Graphs and schemas

Whenever you create a graph, diagram or schema (flowcharts, architectures, state machines, sequence diagrams, dependency graphs, pipelines, etc.), use Mermaid in a fenced ```` ```mermaid ```` block, unless the user specifies another format. Mermaid renders LaTeX via `$$...$$`, so use it for math in node labels and edge text (e.g. `A["$$\alpha + \beta$$"]`).
