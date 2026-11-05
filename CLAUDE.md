# Global instructions

## Writing rules

### References and citations

Make every reference or citation a clickable markdown link, directly in the running text, not only in a bibliography at the end. Link the citation itself, e.g. `([He et al., 2016](https://arxiv.org/abs/1512.03385))` or `([Zhang et al., d2l §8.6.1](https://d2l.ai/chapter_convolutional-modern/resnet.html))`, instead of bare `(He et al., 2016)`.

- Prefer a stable URL: DOI (`https://doi.org/...`), arXiv, publisher page, or the official docs/book section. Link to the specific section when citing a book or docs page.
- Only link URLs you have actually seen (from a search, fetch or the user). Never guess or reconstruct a URL from memory; if you cannot verify one, say the source is unlinked rather than inventing a link.
- If the same source is cited several times, link it each time it appears in a new paragraph.

## Math formatting

Always write mathematical formulas in LaTeX in your responses: use `$...$` for inline math and `$$...$$` for display equations. Do not use plain-text or Unicode approximations (e.g. write `$x^2 + y^2 = r^2$`, not `x^2 + y^2 = r^2` or `x² + y² = r²`).

Never wrap a bare number in math delimiters: the renderer treats `$` followed by a digit as a currency sign and breaks the surrounding formulas. Write plain numbers as plain text (0.90, not `$0.90$`). If a number belongs to a formula, put it inside a full expression that starts with a symbol (e.g. `$p_1 = 0.90$`, `$\text{IoU} = 0.5$`).

Every formula must be followed by a short caption that introduces all of its symbols, so it is understandable, or at least readable, without prior knowledge. Right after the formula, give a "where" line that states what each symbol means (and its shape or domain when that matters), e.g.:

$$\mathbf{y} = \mathcal{F}(\mathbf{x}; \{W_i\}) + \mathbf{x}$$

where $\mathbf{x}$ is the block input, $\mathbf{y}$ its output, $\mathcal{F}$ the residual function learned by the block, and $\{W_i\}$ the weights of $\mathcal{F}$.

- Define every symbol, including indices, sets, operators and constants that are not universally known (e.g. $\pi$ and basic $+$ need no definition, but $\mathcal{F}$, $W_i$ or $\odot$ do).
- Keep the caption to one or two sentences; do not turn it into a derivation.
- This applies to inline formulas too: introduce the symbol the first time it appears (e.g. "the learning rate $\eta$").
- If a symbol was already defined earlier in the same response, do not repeat its definition.

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

For readable layouts, in both fenced blocks and widgets (a wide diagram gets scaled down to fit the available width, which makes its text small):

- Use `flowchart TB` by default, and always for long graphs or for subgraphs with interconnected nodes (e.g. skip connections). If a node inside a subgraph links to something outside it, Mermaid ignores that subgraph's `direction` and uses the outer one, so the outer direction has to be the vertical one.
- Use `flowchart LR` only when a row has at most 4 nodes.
- Subgraphs can sit side by side only if they are linked as a whole by ID (`stem --> stages`) and no inner node links outside its subgraph: use `flowchart LR` on the outside and `direction TB` inside each subgraph.
- Keep labels to a few words, and use `<br/>` to break longer ones.
- If a diagram is still too large to read, split it into an overview plus one diagram per part.

Every diagram that uses technical terms or abbreviations must be followed by a short caption that explains them, as with formulas, so it is understandable, or at least readable, without prior knowledge. Right after the diagram, add a small standalone paragraph that starts with the word "Caption" in italics (`*Caption:*`) and states what each term means, e.g.:

*Caption:* stride is the factor by which a stage has downsampled the input (stride 8 means 8 times smaller), and FC is a fully connected layer.


- Explain every term that is not universally known, including abbreviations and any symbols or formulas in the labels.
- Keep the caption to one or two sentences; do not describe the diagram step by step.
- If a term was already explained earlier in the same response, do not repeat its explanation.
