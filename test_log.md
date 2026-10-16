
# AI Innovator Agent — Evaluation Log

## Run 1 — Baseline

**Design:** Initial Sarvam-powered research agent using a
single generation call and a system prompt prioritizing
official disclosures.

**Result:** Successfully loaded eight documents and generated
a Markdown research brief.

**Issues identified:**
- The promoter-pledging trend was incorrectly described as
  increasing from 11.5% to 4.1%, although this is a decrease.
- A penalty involving a similarly named local cable-TV operator
  was incorrectly presented as a possible risk for the listed
  manufacturer.
- The revenue discrepancy was identified but needed clearer
  treatment as an unresolved conflict.

## Run 2 — Prompt Improvements

**Design change:** Added explicit rules for numerical direction,
company-identity checks, source attribution, and prompt-injection
resistance.

**Result:** The agent handled the unrelated company's identity
more cautiously, but still incorrectly described the promoter-
pledging decrease as an increase.

**Conclusion:** Prompt instructions improved entity handling but
did not reliably prevent numerical-direction errors.

## Run 3 — Draft and Review Pipeline

**Design change:** Added a separate Sarvam review pass and
programmatic validation for the known pledging-direction error.

**Result:** The reviewed report included a dedicated revenue
conflict section, identified the preferred primary disclosure,
and did not attribute the local operator's penalty to the listed
manufacturer. The reversed pledging trend no longer appeared,
but the trend was omitted rather than explicitly explained.

**Remaining limitations:** The report still needed to include
the source-supported pledging trend and correct a reference to
the revenue discrepancy as an "official filing" rather than
the company IR press release.

## Final refinement

Updated the final brief to state the three reported pledging
figures and correct the description of the revenue source.

This was a manual editorial correction following Run 3.
The original generated draft and reviewed output are preserved
in the output directory for comparison.

## Overall learning

The experiments demonstrate that an LLM can identify material
financial conflicts but may make basic numerical-direction
mistakes. A separate review pass improves the result, but
source attribution, deterministic checks, and human review
remain necessary.
