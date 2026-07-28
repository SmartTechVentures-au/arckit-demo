# Tech Note: ASR and Caption Accuracy for Accessibility Conformance

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-TECH-asr-caption-accuracy-v1.0 |
| **Document Type** | Technology Note |
| **Project** | Originated in Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Updated** | 2026-07-27 |
| **Review Date** | 2027-07-27 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies |
| **Confidence** | **HIGH** — grounded in peer-reviewed research and a published industry benchmark |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Learning Innovation, Digital & IT, Accessibility, Procurement |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Summary

Automatic Speech Recognition (ASR) is now bundled into every major video and meeting platform, and vendors routinely market accuracy figures in the 90–95% range. **The independent evidence does not support treating those figures as sufficient for accessibility conformance, and does not support comparing vendors on a single accuracy number at all.** Peer-reviewed measurement across eleven ASR services using higher-education lecture recordings found accuracy varies widely both between vendors *and between individual recordings from the same vendor*, with no vendor consistently best. A large industry benchmark across 205 hours of content found that error rates across all engines still fall short of accessibility requirements. The practical consequence for any procurement or design decision: **specify a fixed, locally built test set drawn from the actual content the system will caption, size it for statistical stability, and never accept a vendor accuracy claim as evidence.**

## Key Findings

### The measurement problem — a single accuracy number is not meaningful

- Kuhn, Kersken, Reuter, Egger and Zimmermann (2024) evaluated **eleven common ASR services** against recordings of Higher Education lectures, motivated explicitly by the gap between industry accuracy claims and accessibility problems reported by Deaf and hard-of-hearing users [ASR-C1].
- Finding: "accuracy ranges widely between vendors and for the individual audio samples", and "despite the recent improvements of ASR, common services lack reliability in accuracy" [ASR-C1].
- Critically: **"even providers that achieve a relatively low average WER can show a high error rate for an individual audio sample"**, and **no vendor consistently reached the lowest WER across all samples** [ASR-C2].
- Performance depended heavily on the individual speaker and the acoustic environment, even where samples did **not** contain strong accents [ASR-C2].
- State-of-the-art average for English is around **5% WER**, with the explicit caveat that results differ for spontaneous, conversational and colloquial speech [ASR-C2] — which is what teaching mostly is.

> **Design implication**: a test set of two or three recordings will produce a *random* vendor ranking. Sizing must reflect the observed sample-level variance.

### Streaming (live) ASR is materially worse than batch

- The same study found **significantly lower quality for streaming ASR, which is used for live events** [ASR-C1].
- Corroborating operational figure: AARNet reports Zoom live transcription at approximately **90% accuracy depending on audio quality and speaker accents**, and notes it does not work in breakout rooms [ZOOM-C1].

> **Design implication**: requirements should state whether an accuracy threshold applies to live captions, post-processed captions, or both. They are different problems with different achievable ceilings.

### ASR alone does not meet accessibility standards — the industry's own benchmark says so

- 3Play Media's **2025 State of ASR** (published 20 May 2025) tested eight ASR engines plus Gemini across **205 hours** of audio and over **1.7 million words** [3P-C1].
- Headline finding: **"error rates across all engines still fall short of meeting accessibility requirements"** [3P-C1].
- Accuracy improvement for English pre-recorded content is **plateauing**; the gap between leading engines and the rest has widened [3P-C1].
- "Human-in-the-loop workflows remain critical for captioning and transcription use cases" [3P-C1].
- The prior-year study was blunter: **"ASR alone is still insufficient for the captioning use case, especially regarding formatting and hallucinations"**, with hallucination (engines generating words not present in the audio) singled out as persistent, particularly in Whisper [3P-C2].
- The 2024 study also argued that Word Error Rate alone is insufficient as a metric, and that evaluation should include **Formatted Error Rate (FER)** and NER-model considerations [3P-C2].

### Domain vocabulary is where ASR fails, and it fails unevenly

- 3Play found accuracy varies significantly **by industry/vertical**, with sports content showing error rates **3× higher** than the best-performing verticals — attributed to noisy environments, unscripted speech, proper nouns (player and coach names), and numerical information with unusual phrasing conventions [3P-C1].
- Research into specialised terminology reports WER ranging **from 0.087 in controlled dictation to over 50% in conversational or multi-speaker scenarios**, with medical communication scenarios between **0.122 and 0.228** [ASRMED-C1].
- Commercial ASR tools "exhibited high word error rates particularly with specialized academic terminology" [ASRMED-C1].

> **Generalisation, flagged as directional rather than measured**: the profile 3Play describes for sports content — unscripted speech, proper nouns, unusual phrasing, imperfect acoustics — matches music performance teaching and clinical teaching closely. A platform's *general* caption score is therefore a poor predictor of its performance on the content where captions matter most.

### Vendor mitigations exist and differ operationally

Custom vocabulary / dictionary support is the standard mitigation, but the **operating model differs and that difference is procurement-relevant**:

- **Self-service, institution-maintained**: Panopto documents site-level custom dictionaries for ASR and OCR covering specialised terms, proper nouns and acronyms [PAN-C1].
- **Vendor-mediated**: Echo360 supports custom transcription dictionaries in AWS Transcribe format, but they "must be configured by Echo360 Support on behalf of institutions" [E360-C1].
- **Confidence thresholds**: Echo360 allows an institution to set a confidence score above which ASR transcripts auto-apply to the caption track [E360-C1] — a useful control for separating "good enough to publish" from "needs review".

Notably, at least one vendor's own documentation concedes the limitation directly: Echo360 states ASR "is unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals" [E360-C1].

### Recommended evaluation method

1. **Build a fixed test set before evaluation**, drawn from real teaching content in the disciplines with the hardest vocabulary.
2. **Size for stability.** Given the documented sample-level variance [ASR-C2], a set of **at least 20 recordings** spanning multiple speakers, multiple rooms and both large and small spaces is a reasonable minimum. *(This sizing is a professional judgement derived from the variance finding, not a figure published in the cited studies.)*
3. **Produce a human reference transcript** for each item.
4. **Reuse the same set every semester** so the measure is a trend, not a one-off.
5. **Measure more than WER** — consider formatting and hallucination separately [3P-C2], since both affect usability without necessarily moving WER much.
6. **Test the custom-dictionary workflow itself**, not just its existence: can the institution add a term today and see the effect on the next recording?
7. **Budget for human correction.** Every independent source concludes human-in-the-loop remains necessary [3P-C1] [3P-C2]. A design that assumes pure ASR will underfund support.

## Relevance to Projects

- **002-lecture-capture** — directly underpins NFR-U-003 (caption accuracy validated against a discipline-vocabulary test set), NFR-C-002 (WCAG 2.2 AA mandatory gate), FR-006, FR-007, dependency D-8 and risk R-018. The evidence here is the justification for D-8 being a blocking evaluation deliverable rather than a nice-to-have.
- **001-lt-ecosystem** — applies to REQ-029 (WCAG 2.2 AA across all student-facing tools) wherever recorded or live media is involved.
- **Any future project** procuring video, meeting, transcription or accessibility tooling. The core conclusion — *vendor accuracy claims are not evidence; build a local test set* — is vendor-agnostic and durable.
- **Accessibility and disability services** generally: the finding that human review remains necessary has resourcing consequences beyond any single platform decision.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | NFR-U-003, NFR-C-002, FR-006, FR-007, D-8 |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| ASR-C1 | Kuhn, Kersken, Reuter, Egger, Zimmermann (2024) — *Measuring the Accuracy of Automatic Speech Recognition Solutions*, arXiv | https://arxiv.org/abs/2408.16287 | Fetched | Eleven ASR services; motivated by gap between industry claims and DHH user experience; "accuracy ranges widely between vendors and for the individual audio samples"; "common services lack reliability in accuracy"; "significant lower quality for streaming ASR, which is used for live events" |
| ASR-C2 | Same study — detailed findings | https://arxiv.org/pdf/2408.16287 | Search result | Higher Education lectures as the use case; "even providers that achieve a relatively low average WER can show a high error rate for an individual audio sample"; no vendor consistently lowest; dependence on speaker and acoustic environment absent strong accents; ~5% WER state of the art for English |
| ASR-C3 | Same paper, published venue — ACM Transactions on Accessible Computing | https://dl.acm.org/doi/10.1145/3636513 | **HTTP 403** — cited via the arXiv version | Peer-reviewed venue reference |
| ASRMED-C1 | Aggregated research findings on ASR accuracy for specialised and medical terminology | https://dl.acm.org/doi/10.1145/3636513 (and related literature) | Search result aggregate | WER 0.087 (controlled dictation) to >50% (conversational/multi-speaker); medical communication 0.122–0.228; "high word error rates particularly with specialized academic terminology". **Aggregated across sources; individual papers not fetched — medium confidence** |
| 3P-C1 | 3Play Media — 2025 State of ASR Report | https://www.3playmedia.com/news/2025-asr-report-release/ | Fetched | Published 20 May 2025; 205 hours, 1.7m+ words, eight engines plus Gemini; "error rates across all engines still fall short of meeting accessibility requirements"; plateau in English pre-recorded accuracy; sports 3× error rate; "human-in-the-loop workflows remain critical" |
| 3P-C2 | 3Play Media — annual State of ASR study (2024) | https://www.3playmedia.com/blog/annual-state-of-asr-study/ | Fetched | "ASR alone is still insufficient for the captioning use case, especially regarding formatting and hallucinations"; hallucination persistent particularly in Whisper; WER insufficient as sole metric — consider Formatted Error Rate and NER model |
| PAN-C1 | Aalto University OPIT — Boost ASR accuracy on Panopto with a Custom Dictionary | https://blogs.aalto.fi/opit/2024/08/12/boost-asr-accuracy-on-panopto-with-a-custom-dictionary-tailored-to-aalto-university/ | Search result | Site-level custom dictionaries for ASR and OCR; institution-maintained |
| E360-C1 | Echo360 Support — ASR Service for Media Transcription | https://support.echo360.com/hc/en-us/articles/360035406171-EchoVideo-Automatic-Speech-Recognition-ASR-Service-for-Media-Transcription | Fetched | AWS Transcribe; confidence-score threshold for auto-applying captions; custom dictionaries "must be configured by Echo360 Support on behalf of institutions"; ASR "is unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals"; WEBVTT caption/transcript format |
| ZOOM-C1 | AARNet — Zoom introduces Live Transcription, and Cloud Recording storage in Australia for education | https://www.aarnet.edu.au/zoom-introduces-live-transcription-and-cloud-recording-storage-in-australia-for-education | Fetched | Live transcription approximately 90% accuracy depending on audio quality and speaker accents; not available in breakout rooms; transcripts saveable alongside recordings |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
