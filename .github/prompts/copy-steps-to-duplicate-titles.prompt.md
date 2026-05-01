---
agent: "agent"
model: "GPT-5 (copilot)"
description: Copy steps arrays from the first instance of a named move to all later files with the same title.
---

For each file in `content/moves/*/index.md`, sorted by the numeric folder name ascending, do the following:

1. Parse the frontmatter of every file to extract `title` and `steps`.
2. Build a lookup table of **first-seen title → steps array**, but only record an entry when the steps array for that title is non-empty (i.e. it contains at least one item). Process files in ascending numeric folder order so the earliest-numbered file wins.
3. For every file whose `title` already exists in the lookup table **and** whose own `steps` array is currently empty (`steps: []`), replace the empty `steps: []` with the steps array from the lookup table entry. **Write the replacement in inline array format on one line only**, e.g. `steps: [Step one, Step two]`.
4. Formatting requirements are strict: keep `steps` as a single-line inline array in all edits, do not convert it to YAML block-list style (`steps:` with `- item` lines), and preserve all other frontmatter fields exactly as they are.
5. After all updates are complete, output a list of every file path that was changed, grouped by the shared title. If no files were changed, say so explicitly.
