---
agent: "agent"
model: "GPT-5 (copilot)"
description: Copy steps arrays from the first instance of a named move to all later files with the same title.
---

For each file in `content/moves/*/index.md`, sorted by the numeric folder name ascending, do the following:

1. Parse the frontmatter of every file to extract `title` and `steps`.
2. Build a lookup table of **first-seen title → steps array**, but only record an entry when the steps array for that title is non-empty (i.e. it contains at least one item). Process files in ascending numeric folder order so the earliest-numbered file wins.
3. For every file whose `title` already exists in the lookup table **and** whose own `steps` array is currently empty (`steps: []`), replace the empty `steps: []` with the steps array from the lookup table entry. Preserve all other frontmatter fields exactly as they are.
4. Do not modify any file whose steps array is already non-empty. Do not delete any steps arrays. Only add steps arrays where they are missing, and only if we have seen a non-empty steps array for that title in an earlier file.
5. After all updates are complete, output a list of every file path that was changed, grouped by the shared title. If no files were changed, say so explicitly.
