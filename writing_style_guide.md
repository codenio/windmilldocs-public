# Writing style guide

This file contains writing style guidance when creating Windmill documentation. Review this guide before writing documentation.

## General writing style issues

### Overly marketing language

**Problem example:**
"Windmill can automatically fill your script and flow input forms using AI to save you time and effort. This intelligent feature analyzes your form parameters and can populate them with contextually appropriate values based on your requirements."

**Issues:**

- Too long and verbose for technical documentation
- Marketing language like "This intelligent feature" sounds promotional rather than technical
- Users prefer concise, direct explanations over flowery descriptions
- No backlinks to other pages of documentation

**Better approach:**

- Keep descriptions short and technical
- Focus on what the feature does and how to use it, not how "intelligent" or "smart" it is
- Use straightforward language: "Windmill can auto-fill [script](../script_editor/index.mdx) and [flow](../flows/flow_editor/index.mdx) inputs using AI" instead of verbose marketing copy

## Technical blog posts

Long-form technical posts (comparisons, deep dives, launch write-ups) follow everything above, plus the rules below. These are distilled from real editing feedback. The target is a dry, partisan-but-precise engineering voice, not marketing. Read each sentence and ask "does this state a fact, or sell a feeling?" - delete the ones that sell.

### Voice

- Use "we" (the company/team), never "I" or "the founder". First-person-singular reads as a personal blog; keep it collective. (Quoted developer questions like "how do I dedup here?" are fine.)
- Being partisan is fine when the post says so up front, but every claim must be checkable and specific about the gaps. Credit competitors plainly and accurately.

### Cut marketing and AI tone

- No hype adjectives: "excellent", "arguably the best in the space", "rich", "powerful", "seamless", "blazing fast". State what it does instead.
- No AI scaffolding phrases: "This is the part most people will want to see", "The power is that…", "The mechanism is the interesting part", "Two things are easy to miss and both matter", "worth pulling out", "Here's the thing".
- No self-congratulation or performative winks: "the crux of the whole argument", "that last point is the tell", "a post that told you otherwise would deserve the comments it got", "and more interesting".
- No clichés: "went the extra mile", "at the end of the day", "the magic is".
- Drop softeners and filler openers: "If you take one thing away:", "it's worth seeing where", "is a supported path, not a demo", "Look at…".
- Prefer natural phrasing over stiff self-labels ("This is a long, mechanical post" reads awkwardly; "This post is long and detailed" is fine).

### Claims

- Prefer grounded, bounded claims over sweeping superlatives: "deeper than the current state of the art" beats "deeper than anything else we know of".
- Back non-obvious claims with a link to an authoritative source rather than asserting them (e.g. "most data pipelines are small data" → a cited essay).
- Don't imply product history that doesn't exist. For a day-0 feature, present it as it is; never "X started as Y, that was a gap, now it's fixed" or "it used to be a gap, it no longer is".

### Conclusions

- Land a clear, affirmative-but-measured verdict and name the one or two real holdouts honestly. Don't hedge into mush, and don't dump a superlative feature-list run-on - if the intro promises "not a feature grid", keep that promise.

### Diagrams

- Reach for a diagram whenever the point is structural or spatial (a layered stack, an indirection/delegation chain, copy-on-write forks). Prose forces the reader to rebuild the picture in their head; a figure just shows it.
- Keep figures clean: avoid many bordered boxes/chips. Flatten repeated items to plain text lines; reserve one accent color per meaning; use a single thin left accent bar for callouts instead of full outlines.
- Match the product's real UI where relevant (e.g. reuse the actual graph chip colors) so the figure doubles as a legend.
- Author as SVG with the brand tokens from the `blog-thumbnail` skill, rasterize to `.webp` + `.png` next to the post, and reference the raster in the MDX.

### Symmetry and accuracy

- If you show one side's generated/compiled output, show the other's too (e.g. dbt's compiled MERGE alongside Windmill's codegen), so the comparison is fair.
- Get the architecture right before asserting it: distinguish control/orchestration from execution/data flow, and verify relationships rather than assuming them.