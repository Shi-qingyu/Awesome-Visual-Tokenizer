# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository nature

This is a curated paper list (awesome-list style), not a code project. The entire content lives in `README.md` — there is no source code, no build system, no tests, and no tooling. Most tasks will be: adding a new paper to the right section, fixing a link, or reorganizing entries within the taxonomy.

## Taxonomy structure

The README is organized as two top-level groups, each with sub-sections. Putting a new paper in the right sub-section is the main editorial decision.

- **Task-Specific Tokenizers** — tokenizers designed for perception, reconstruction, or compression only.
  - *Variational / Continuous Foundations* — VAE-family and continuous-latent foundations (KL-regularized, hierarchical, flow-based).
  - *Quantization / Discrete Foundations* — discrete codebooks: VQ-VAE/VQGAN lineage, FSQ/BSQ scalar/binary quantization, residual/product quantization.
  - *Compression / Generation-Oriented Tokenizers* — heavily compressed or generation-tuned tokenizers (1D tokens, deep-compression AEs, diffusion autoencoders, etc.).
- **Unified Tokenizers** — tokenizers intended to support *both* visual understanding and generation. Sub-axis is the encoder topology:
  - *Single Encoder: Enhancing Semantics* — one encoder, semantics added/scaled on top of a reconstruction tokenizer.
  - *Single Encoder: Preserving Semantics* — one encoder built on a frozen/pretrained semantic backbone (CLIP/DINO/etc.), tokenizer adapts around it.
  - *Dual Encoder: Parallel* — two encoders run side-by-side (e.g., a semantic + a reconstruction branch combined).
  - *Dual Encoder: Cascade* — two encoders chained (one feeds the other).
  - *Unified Multimodal Systems Using Separated Visual Tokenizers* — full MLLM systems where understanding and generation each get their own tokenizer.

A paper can legitimately appear in more than one section (e.g., `VFMTok`, `ImageFolder` already appear twice). Don't deduplicate aggressively — if a paper has two distinct angles, both placements are intentional.

## Table format

Every section is a single Markdown table with exactly these columns:

```
| Alias | Paper | Link | Code / Project |
```

Conventions to preserve when editing:

- **Alias**: short model name (e.g., `VQ-VAE`, `MAGVIT`). Use `-` if the paper has no commonly-used short name.
- **Paper**: full title, no trailing period.
- **Link**: `[Paper](arxiv-url)` — prefer arXiv abs URLs. Use `-` only when no public link exists at all.
- **Code / Project**: `[org/repo](github-url)` for code, `[Project Page](url)` for project sites. Use `-` when nothing public is available — this is meaningful and explained in the README's "Notes" preamble.
- New entries are generally appended to the bottom of the relevant table (the existing ordering is roughly chronological by publication, but not strictly enforced).

## Editing checklist

When asked to add a paper:

1. Decide the section from the taxonomy above (ask if it's genuinely ambiguous between Task-Specific vs Unified, or which encoder topology applies).
2. Append a new row to that section's table, matching the column conventions exactly.
3. Don't invent links — if the user didn't provide a code URL, use `-`.
