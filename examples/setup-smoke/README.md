# Instagram Reels setup smoke test

This is a technical setup test, not an approved episode or a channel mascot. It exercises the chosen workflow: GPT Image online, Russian Qwen3-TTS and Whisper locally, captions, generated music and a draft MP4. The script uses a 9:16 canvas, `safe: reels` and 30 fps; `--draft` deliberately renders at half size and 15 fps.

The reference used for the voice is the synthetic Qwen3 narrator from `examples/ai-jobs/assets/voice/`, restored by `npm run assets:fetch`. It is the exact reference identified in [narrator provenance](../../production/voices/references/ru-qwen3-narrator.json). This test explicitly uses Qwen3 and does not change the repository's selected default for other episodes.

## Results on Apple M3 Pro, 18 GB, 1 November 2026

- An image was created with the built-in GPT Image tool and adapted to 1152×2048. [images.json](images.json) records the actual prompt, tool, dimensions and SHA-256; the image model version was not exposed by the tool, and its seed is not reproducible. The [small preview](preview/hello.jpg) is in Git. The full image is excluded by the media policy.
- Qwen3 produced 6.757 seconds of narration, with all 12 script words aligned by Whisper. The finished mix transcribed as: «Привет! Здесь рождаются маленькие истории. Яркие картинки, выразительный голос и немного музыки.»
- The first run produced a 7.86-second timeline, a 540×960, 15 fps draft MP4, a web copy and SRT/VTT subtitles. FFmpeg decoded the MP4, and a frame was inspected. The music/voice mix measured −14.0 LUFS and −1.2 dBFS peak.
- The tracked example was subsequently rendered again using the restored Qwen3 reference and the locally copied original picture: the same narration and timeline lengths, master and web MP4s, and subtitles were produced.
- This was a draft: the release QA and editorial approval were not performed. ASR alignment is not a judgment of pronunciation, story quality or suitability for publication; listen to the narration and review the final export.

## Run on a fresh checkout

Follow [the machine setup](../../docs/reference/smart-little-toons-setup.md), then restore the reference inputs with `npm run assets:fetch`. The original `shots/hello.png` is intentionally not in Git. On the machine that made the test, copy it from the ignored `private/local-setup-smoke/shots/hello.png` to `examples/setup-smoke/shots/hello.png`. Otherwise, generate an image from the recorded prompt using an available GPT Image tool, save it at that path, and update `images.json` with the actual tool/model information and SHA-256. Online generation does not reproduce the original image from its recorded seed.

```sh
npm run storygro -- images examples/setup-smoke/ru.reel.yaml --dry-run
npm run storygro -- voice  examples/setup-smoke/ru.reel.yaml
npm run storygro -- board  examples/setup-smoke/ru.reel.yaml
npm run storygro -- render examples/setup-smoke/ru.reel.yaml --draft
```

Outputs live under the ignored `examples/setup-smoke/.reel/ru/`. These commands do not publish anything or record owner approvals. Before actual production, use a new episode in `content/videos/`, prepare sources and facts where needed, and follow the [review workflow](../../docs/explanation/content-workflow.md).
