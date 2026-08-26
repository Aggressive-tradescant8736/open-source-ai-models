# Contributing

Thanks for helping build a directory that's actually useful. This project prioritizes accuracy and usefulness over the number of entries — please read this before opening a PR.

## Before adding a model

1. Verify the official project (GitHub, Hugging Face, or project site).
2. Verify the model name (exact, including version).
3. Verify the license — link to the actual license file/page.
4. Verify the model's intended task/category.
5. Verify parameter count, if applicable.
6. Verify model size, if available.
7. Verify hardware requirements, if available (never guess VRAM numbers).
8. Add the correct category and subcategory (see the numbered sections in `README.md`).
9. Add the official source link (GitHub > Hugging Face > project site > docs > paper — in that priority order).
10. Avoid unsupported claims (no invented benchmarks, no marketing language).

If a piece of information is genuinely unavailable, write `N/A` — do not guess or leave it blank.

## Where model data lives

Everything lives directly in `README.md` — there is no separate `data/` folder. Find the numbered category section that matches your model (e.g. `## 2. Coding`) and add a row to its table. If your model doesn't fit an existing category, propose a new numbered section (keep the taxonomy in mind: General AI, Coding, Computer Vision, Document AI, Image Generation, Video, Audio & Speech, Multimodal, Retrieval, Language, Agents, Lightweight & Edge AI).

Only touch the **Featured** section at the top if your addition genuinely belongs in a "Best of" pick, with a clear documented reason (benchmark, license advantage, hardware tier it uniquely fills).

## Entry format

LLMs and text models:

```markdown
| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| Model Name | 7B | 128K | ~8 GB | Apache-2.0 | Coding |
```

Vision / audio / non-LLM models:

```markdown
| Model | Size | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| Model Name | ~200 MB | Matting | CPU/GPU | MIT | Background Removal |
```

Keep a short "Notes" section under each table for context that doesn't fit a cell (architecture quirks, license caveats, related variants).

## License labels

Use one of: `Open Source`, `Open Weight`, `Research Only`, `Commercial Allowed`, `Commercial Restricted`, `Unknown` — alongside the exact license name when known (Apache-2.0, MIT, Llama License, Gemma Terms, custom, etc.). Never call a model "open source" just because the weights are downloadable — if it's a custom/restrictive license, say so.

## Pull requests

Every PR adding a model should include this in the description:

```text
Model:
Category:
Official Source:
License:
Why should this model be included?
```

- Split large bulk additions into logical commits (e.g. one commit per category or per model family) where possible.
- Do not add duplicate entries unless they represent genuinely different models or variants.
- If updating an existing entry: preserve existing formatting, don't remove useful information without reason, check whether the official project has released a newer version, and update broken links.

## Model selection criteria

We weigh: relevance (solves a real problem), accessibility (can developers actually get and run it), documentation quality, license clarity, community adoption, demonstrated performance, and maintenance activity. When in doubt, prefer a smaller list of well-documented models over padding the directory.

## Reporting issues

Use the issue templates in `.github/ISSUE_TEMPLATE/` for outdated info, broken links, or new model requests.
