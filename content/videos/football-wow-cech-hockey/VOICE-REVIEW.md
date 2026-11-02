# Voice review — Petr Čech

1 November2026. New episode, not a replacement of the delivered Kane masters.

The narrator uses the exact original synthetic OmniVoice B reference SHA-256 `28881ea9cd8050a244837853a834c462df41e7889883f0ad2c699f686719f934`. Base whole-sentence performances are slowed to0.96 with pitch preserved; previous Kane0.82 is slower. This new episode's duration request and verbatim text determine its pace. Global preferences and original reference are unchanged. No interior silence was inserted through speech.

Matvey C / Sofia A references are unchanged. New replies use the exact selected references with Qwen3-TTS Base bf16 at speed1.0; the Kane clips themselves are not reused because this episode has different dialogue. Audio/source SHA-256 records and synthesis text are in assets/voice/provenance.json. Choosing the reference does not certify the new full performance.

Imported dialogue is re-aligned using Whisper. All scenes have exact word alignment1.0 except the opening0.909: independent ASR confirms all words and splits «вау-факт» into «вау» / «-факт». This is a tokenisation difference, not an omitted word. On-screen wording was mechanically compared to the owner's text; only the explicitly authorised copied source marker is excluded. Numbers retain their original writing; spoken number expansions and Russian hints for the English club names are separate in the script and provenance.

Pronunciation norms: голки́пер ([Грамота](https://gramota.ru/meta/golkiper)); коньки́ ([Russian orthographic dictionary](https://gramota.ru/storage/public/normdicts/orfograficheskij_slovar.pdf)); воро́та is the already sourced shared lexicon entry. Direct dictionary pages returned403 during this run, so this document does not claim a fresh complete dictionary audit. Contextual Cyrillic hints for Guildford Phoenix and Haringey Huskies are recorded in the actual synthesis job. Do not silently add a permanent club-name stress rule based only on the agent's transliteration.

The cached wav2vec2 phoneme model was run against actual contextual clips for Петр,Чех,голкипером,коньки,ворота,буллитов and both club names. Evidence is retained locally in private/cech-production-2026-11-01/phoneme-evidence.json and included in the delivery. It supports word/form review but does not establish every stress or natural intonation. In particular, vowel length is not by itself a stress certificate.

The final mixed film receives the repository's separate ASR/QA pass. The agent has not claimed full subjective listening. Owner full-film viewing/listening, including stresses, intonation and both new host performances, remains pending; no release approval or publication is recorded.

The repository's read-only `stress --lookup` additionally retrieved Че́лси,Арсена́л,Ги́лфорд,Фе́никс and the English-word rendering Ха́скис. These sourced norms are recorded in the shared lexicon with `mark:false`, so no performance or global voice setting changes. Haringey was not found and remains a contextual pronunciation hint rather than a certified permanent dictionary rule. The final mix ASR pass matched100% in every scene; that result still does not certify all stresses.
