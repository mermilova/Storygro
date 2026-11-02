# Football starter kit on Marina's workstation

Verified on 1 November 2026, Apple M3 Pro with 18 GB RAM. This records local preparation for Instagram channel `smart_little_toons`; it is not an episode or release approval.

## Checkout and inputs

The existing `Storygro/` checkout stays on `main`. A sibling Git worktree, `Storygro-football/`, uses branch `marina/football-preparation`, based on upstream `series/football-legends` commit `bba07e0a0826b90b478feb9e7ce10410b080c0ab`. Run this series' commands through `npm run storygro -- …` inside that worktree, so a global CLI does not select an older engine. Push workstation changes to the user's fork `mermilova/Storygro`.

The supplied `Storygro-Marina-starter-2026-11-01` kit contains Yashin and Sivori videos, original episode pictures, approved Matvey/Sofia references, synthetic voice references, scripts and source records. All 134 files passed the supplied manifest's byte-size and SHA-256 checks, both before and after copying to local workspace storage. The inspected restoration script restored 40 files and reused 10 identical files. Existing differing files were not replaced; the kit's source documents did not overwrite the branch's tracked scripts.

A separately supplied Matthews MP4 and two decorative PNGs were also copied and hashed. The approved identity references remain `content/series/football-legends/cast/`; the decorative PNGs do not replace them. The materials catalogue, intake manifest, original kit and review artifacts live outside the checkout in the workspace's `materials/` directory. Those local files are not part of a Git clone.

## Verified environment

- Node dependencies installed with `npm ci`; `zod` updated from 4.6.5 to 4.6.7, matching the earlier workstation fix on `main`. Audit reported zero vulnerabilities.
- Full `npm run check` passed: media policy, documentation links, TypeScript and 133 tests.
- `uv pip check` passed for the existing isolated OmniVoice environment; PyTorch 2.14.1 reports MPS available. Existing Python environments were retained.
- Qwen3, Whisper and RUAccent were already available from the initial workstation setup. Illustration generation uses online built-in GPT Image; local image models are not required. Record the actual tool and exposed model information, without inventing an image-model version or starting nested Codex workers without delegation authorization.

## Exact OmniVoice B restored and tested

The kit supplied the previously missing original `ru-omnivoice-b.wav`, with matching text and provenance. Its SHA-256 is `28881ea9cd8050a244837853a834c462df41e7889883f0ad2c699f686719f934`. Exact copies now exist in both checkouts' `production/voices/references/` and `~/.storygro/voices/`. No voice was regenerated or substituted, and shared voice preferences and existing episode settings were preserved.

The complete `k2-fsa/OmniVoice` snapshot `c5fdb5ccb189668d56333f77ba2629f4cd7535f4` was downloaded. The model, audio tokenizer and text tokenizer were hashed against the Hugging Face file manifest:

| File | Bytes | SHA-256 |
|---|---:|---|
| `model.safetensors` | 2450344112 | `730839316de585f4c8298ec0e1712efc10fb19c6fa4e36eb741cb8d51ebcf6aa` |
| `audio_tokenizer/model.safetensors` | 805665628 | `fe7c5e8785e0a05833e1bfc3e002ec7f55af21e306b2e7154a448c1f54ccfb0d` |
| `tokenizer.json` | 11423986 | `408f669b7e2b045fdf54201d815bd364e6667dbd845115da81239c40bc6dcfd1` |

Offline synthesis through `production/py/voices/omnivoice.py` passed on MPS with the exact B reference, no stress markup and pitch-preserving playback tempo 0.90. Test text: «Матвей и София знакомятся с легендами футбола. Главное — помогать своей команде.» The output is 5.563 seconds at 24 kHz; SHA-256 `5e49fda6b4fa51c3af959cbc07c7b7e1a08020ba3fc114c19f508706856ae237`. Local Whisper reproduced every word after punctuation normalization. This confirms synthesis and text completeness, not correct stress or owner preference after listening.

The test audio and result JSON remain in ignored `private/starter-voice-smoke/`. Download logs, checksums and the test runner remain in the workspace's `.setup-downloads/`, outside Git. OmniVoice model weights retain their separate CC-BY-NC terms; see [voices](voices.md).

## Reference checks and next step

All three supplied MP4s fully decoded without errors: Matthews 87.04 s, Sivori 81.34 s, Yashin 90.20 s; all H.264, 1080×1920, 30 fps. Sampled frames, Yashin/Sivori opening frames and cast references were visually inspected. Whisper transcripts were saved in ignored `private/starter-reference-analysis/`. Approximate analyzer estimates were 113–121 words/minute; name transcription errors remain visible and these values are not a pacing requirement.

Yashin's storyboard rebuilt with `board --no-voice` using restored pictures; a rendered frame was inspected. This uses estimated timing and is not a new narrated render or full release QA. No scene, timing or runtime code changed, so a new full-film render was not required for this setup change. Complete subjective listening and editorial approvals remain pending.

No new topic was supplied. Follow the [series recipe](../how-to/football-series.md), [retention direction worksheet](../how-to/reels-retention.md) and [content approvals](../explanation/content-workflow.md). Earlier examples may predate current first-frame identity rules. New episodes require their own research, direction and script before asset production; preserve the selected calm voice and approved hosts. Generated pictures, audio, MP4s and model files stay outside Git. Social publication remains a separate user operation.
