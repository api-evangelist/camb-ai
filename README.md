# Camb.AI (camb-ai)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Camb.AI is a generative voice AI platform for translation, dubbing, and speech. Its research models - MARS (text-to-speech and voice cloning) and BOLI (neural translation) - power an API covering text-to-speech, end-to-end video and audio dubbing, text translation across 140+ languages, voice discovery and custom voice cloning, and speech-to-text transcription.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/camb-ai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/camb-ai/refs/heads/main/apis.yml)

## Access Model

Camb.AI is a commercial SaaS. The REST API lives at `https://client.camb.ai/apis` and is authenticated with an `x-api-key` header (keys are issued from your Camb.AI account). Most operations are **asynchronous**: you POST to start a task and receive a `task_id`, then GET `/{resource}/{task_id}` and poll until the status is `SUCCESS`, then retrieve the result (audio, transcript, or translation). Streaming text-to-speech (`POST /tts-stream`) instead returns a binary audio stream directly.

Camb.AI **also exposes public WebSocket channels** (`wss`) for real-time work: live streaming TTS, live transcription, and realtime speech-to-speech translation. These are modeled in a companion AsyncAPI document.

Pricing is a six-tier monthly (or discounted annual) subscription (Free through Expert), each bundling a monthly allowance of **credits** that are consumed across all products. Official SDKs are published for Python, TypeScript, Go, Java, PHP, and Rust at [github.com/Camb-ai](https://github.com/Camb-ai). The MARS and BOLI models are proprietary hosted services and are not self-hostable.

## Tags

- AI
- Text to Speech
- Dubbing
- Translation
- Transcription
- Voice Cloning
- Speech

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Camb.AI Text-to-Speech API

Convert text into natural speech with the MARS voice models. Includes a streaming endpoint (`POST /tts-stream`) that returns a binary audio stream, a deprecated task-based create endpoint (`POST /tts`), status polling (`GET /tts/{task_id}`), and audio retrieval (`GET /tts-result/{run_id}`), plus a public WebSocket for real-time low-latency synthesis with optional word-level timestamps.

- **Human URL:** [https://docs.camb.ai/api-reference/endpoint/create-tts-stream](https://docs.camb.ai/api-reference/endpoint/create-tts-stream)
- **Base URL:** `https://client.camb.ai/apis`

### Camb.AI Dubbing API

End-to-end video and audio dubbing that preserves emotional delivery. Submit a media URL with a source language and one or more target languages (`POST /dub`), poll the task (`GET /dub/{task_id}`), then retrieve the dubbed outputs and translated transcripts per target language.

- **Human URL:** [https://docs.camb.ai/api-reference/endpoint/end-to-end-dubbing](https://docs.camb.ai/api-reference/endpoint/end-to-end-dubbing)
- **Base URL:** `https://client.camb.ai/apis`

### Camb.AI Translation API

Neural text translation powered by the BOLI model across 140+ language pairs, with controls for formality, gender, and specialized vocabulary. Start a translation task with an array of texts and source/target locale tags (`POST /translate`), then poll the task (`GET /translate/{task_id}`) for the result.

- **Human URL:** [https://docs.camb.ai/api-reference/endpoint/create-translation](https://docs.camb.ai/api-reference/endpoint/create-translation)
- **Base URL:** `https://client.camb.ai/apis`

### Camb.AI Voices API

Discover and manage the voices used across TTS and dubbing. List public, shared, and custom voices (`GET /list-voices`), clone a custom voice from reference audio (`POST /create-custom-voice`), design a brand-new voice from a text description (`POST /text-to-voice`), and delete a custom voice (`DELETE /delete-voice/{voice_id}`).

- **Human URL:** [https://docs.camb.ai/api-reference/endpoint/list-voices](https://docs.camb.ai/api-reference/endpoint/list-voices)
- **Base URL:** `https://client.camb.ai/apis`

### Camb.AI Transcription API

Speech-to-text transcription with speaker identification and word-level timestamps. Submit a media file or media URL with a language tag (`POST /transcribe`) and poll the task (`GET /transcribe/{task_id}`) for the transcript, or stream audio over a public WebSocket to receive cumulative interim transcripts and typed events in real time.

- **Human URL:** [https://docs.camb.ai/api-reference/endpoint/create-transcription](https://docs.camb.ai/api-reference/endpoint/create-transcription)
- **Base URL:** `https://client.camb.ai/apis`

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/camb-ai)
- [Website](https://www.camb.ai)
- [Documentation](https://docs.camb.ai)
- [Source Code](https://github.com/Camb-ai)
- [Plans](plans/camb-ai-plans-pricing.yml)
- [Rate Limits](rate-limits/camb-ai-rate-limits.yml)
- [Fin Ops](finops/camb-ai-finops.yml)
- [Blog](https://www.camb.ai/blog)

## Artifacts

- [OpenAPI](openapi/camb-ai-openapi.yml) — REST API
- [AsyncAPI](asyncapi/camb-ai-asyncapi.yml) — realtime WebSocket channels
- [Postman Collection](collections/camb-ai.postman_collection.json)
- [Open Collection](collections/camb-ai.opencollection.json)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
