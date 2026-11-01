# Instagram Reels workstation: setup and verification

> Snapshot: 1 November 2026 · Apple M3 Pro, 18 GB · macOS arm64 · `smart_little_toons` Instagram Reels

The local production path is ready for a first brief: online GPT Image creates illustrations; Qwen3-TTS, Whisper, score, captions and MP4 rendering run on this Mac. The [setup smoke test](../../examples/setup-smoke/README.md) records the test script, image provenance, preview and results. It is a technical draft, not an approved release.

## Installed and checked

| Component | Checked version / state |
|---|---|
| Git / Node / npm / uv | Apple Git 2.54.0 / Node 22.23.4 / npm 10.9.9 / uv 0.13.6 |
| Python / FFmpeg | Python 3.12.16 / imageio-ffmpeg 0.7.0 with FFmpeg 7.1 |
| Browser | Existing Google Chrome, used for frames and storyboard |
| Russian voice and speech check | mlx-audio 0.6.3, Qwen3-TTS Base bf16, mlx-whisper 0.4.3, Whisper large-v3-turbo, RUAccent 1.5.8.3 and its dictionaries |
| Illustrations | Built-in GPT Image tool online; the tool did not expose the exact underlying model version. No local image model is needed. |
| Checks | `npm run check`: 110 tests, TypeScript, documentation links and indexed-media policy; `npm audit`: zero vulnerabilities; `uv pip check`: compatible voice environment. |

The exact observed voice environment is captured in [macos-arm64-py312-2026-11-01.txt](../../production/requirements/macos-arm64-py312-2026-11-01.txt). It is a platform-specific package snapshot with pinned versions, not a hash-locked or cross-platform guarantee. The existing [setup script](../../production/scripts/setup.sh) installs compatible current releases and may resolve newer packages.

The snapshot was also installed into a separate fresh Python 3.12.16 environment from the existing uv cache. `uv pip check` passed and imports of mlx-audio, mlx-whisper, RUAccent and imageio-ffmpeg succeeded. This checks package restoration; voice synthesis was tested separately in the original workstation environment.

## Restore a fresh Apple-silicon workstation

Install Node 22.12 or newer, Git, Chrome or Chromium, and uv. In the checkout, run:

```sh
npm ci
npm run hooks:install
npm run check
uv venv --python 3.12.16 "$HOME/.storygro/venv"
uv pip install --python "$HOME/.storygro/venv/bin/python" -r production/requirements/macos-arm64-py312-2026-11-01.txt
uv pip check --python "$HOME/.storygro/venv/bin/python"
npm run assets:fetch
```

Create the Python environment only at a new location; preserve an existing `~/.storygro/venv` and use `STORYGRO_HOME` if a separate setup is needed. The `assets:fetch` command checks SHA-256 and does not silently replace a different file. Model weights are separate from Python packages and download on first use: Qwen3-TTS Base bf16, Whisper large-v3-turbo and RUAccent's local data. The original GPT Image asset is also separate from Git; see the smoke-test README for its restoration and generation limits.

New Russian scaffolds currently select OmniVoice B as specified in [voice preferences](../../production/voices/preferences-ru.yaml). Its exact original reference is absent from the published assets, so an unchanged new scaffold cannot synthesize it on this fresh machine. The tested smoke script explicitly uses the released Qwen3 reference instead; for a new episode choose the voice explicitly and copy its matching WAV and transcript. Never substitute another voice under the OmniVoice B name. Selection of a final narrator still requires listening.

For illustrations use the available GPT Image tool online and save generated files under the episode's ignored `shots/`; retain the prompt, the actual tool/model information and checksums in `images.json`. `images.provider: codex` supports the repository's Codex integration, but its `images.model` field controls the Codex worker model, not the version of GPT Image. The built-in tool may not report or allow selecting its underlying image model; do not assert a specific version without evidence.

Keep credentials, Python environments, models, original generated media, audio, PDF and MP4 outside Git. Sources, prompts, small previews, the package snapshot and test results belong in Git under the [media policy](media-policy.md). Instagram upload remains manual; no account or automated publisher was configured.
