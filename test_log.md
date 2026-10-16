
# AI Innovator Agent — Evaluation Log

## Run 1 — Baseline

**Design:** Sarvam-powered research agent using a system prompt
to prioritize official disclosures and produce a research brief.

**Result:** Successfully processed all eight documents.

**Issues identified:**
- Detected conflicting revenue figures but needed stronger
  handling of source reliability.
- Incorrectly described promoter pledging as increasing from
  11.5% to 4.1%, although the figures show a decrease.
- Incorrectly associated a penalty involving a similarly named
  local cable-TV operator with the listed company.

## Run 2 — Prompt Improvements

**Design change:** Added explicit instructions for checking
numerical directions, distinguishing company identities,
attributing claims, and resisting embedded document instructions.

**Result:** The report handled the unrelated-company issue more
cautiously, but still described promoter pledging as increasing
from 11.5% to 4.1%.

**Learning:** Prompt instructions alone did not reliably prevent
numerical-direction errors.

## Run 3 — Separate Review Pass

**Design change:** Added a second Sarvam call to review the
draft against the source documents and a programmatic check
for the known promoter-pledging direction error.

**Result:** The reviewed report included a dedicated revenue
conflict section, preferred the company IR press release as the
primary source, and did not attribute the local operator's
penalty to the listed manufacturer. The latest generated report
omitted the promoter-pledging trend rather than fully explaining
it.

**Remaining limitations:** A second review pass does not
guarantee factual accuracy. The report still required a manual
editorial correction to include the complete pledging trend.

## Final Editorial Correction

The final research brief was manually edited to include the
source-supported promoter-pledging figures of 11.5% in June
2025, 6.0% in March 2026, and 4.1% in June 2026, and to clarify
that the revenue discrepancy refers to the company IR press
release versus a news article.

## Overall Conclusion

The experiments demonstrate that an LLM can identify important
financial information and source conflicts but may reverse
numerical trends or omit relevant evidence. Source attribution,
deterministic validation, and human review remain important.
