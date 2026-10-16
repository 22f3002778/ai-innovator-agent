# AI Innovator — Sarvottam Cables Research Agent

A small Python research agent that uses Sarvam AI to produce a Markdown brief from a local pack of company documents. The assignment company and sources are fictional; this project intentionally does not fetch live information.

## Features

- Reads local `.md`, `.txt`, `.csv`, and `.json` source documents.
- Uses a separate `system_prompt.txt` file to define research and source-handling rules.
- Generates an initial research brief with Sarvam AI.
- Runs a second model call to audit and revise the draft against the source pack.
- Runs a deterministic validation for a known high-impact numerical-direction error in the promoter pledge data before saving the final report.
- Preserves the draft, reviewed brief, and final brief separately in `output/`.

## Requirements

- Python 3.10 or newer
- A Sarvam AI API key with access to the configured model
- The eight assignment source documents in the `documents/` folder

## Setup

Create and activate a virtual environment if you have not already:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install sarvamai python-dotenv
```

Create a `.env` file in the project root:

```dotenv
SARVAM_API_KEY=put_your_key_here
```

Never commit `.env` or share your API key.

Place all eight assignment source documents inside `documents/`. This version reads Markdown, TXT, CSV, and JSON files.

## Run

```bash
python main.py
```

The program prints the final reviewed brief and writes:

- `output/run3_draft.md` — first model draft
- `output/run3_reviewed.md` — brief after the review pass and validation
- `output/srvcable_research_brief.md` — final output path required by the project

If the deterministic validation detects a known incorrect pledge-direction claim, the program stops instead of saving that result as final. Review the output, improve the prompt or review step, and rerun.

## Model and design rationale

The project uses Sarvam AI's `sarvam-105b` chat completion model. Sarvam is used because it is the selected API provider for this implementation. A two-pass approach was added after the initial single-pass system produced a numerical-direction error: the first pass drafts the brief, while the second pass checks the draft against the same evidence. A deterministic validation acts as a narrow guardrail for the known promoter pledge comparison.

## Limitations

- Both LLM passes can still make mistakes or agree with an incorrect claim.
- The deterministic validation only covers specified checks; it is not a general financial audit.
- No browsing or external verification is performed.
- Only Markdown, TXT, CSV, and JSON files are supported in this version.
- The fictional case should not be treated as real investment research.
