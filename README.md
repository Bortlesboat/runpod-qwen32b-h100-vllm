# Qwen 2.5 32B H100 Worker For RunPod Hub

This repo packages an OpenAI-compatible `vLLM` worker around `Qwen/Qwen2.5-32B-Instruct` for H100-class RunPod Serverless deployments.

It is meant for teams that want a sharper default than a generic `vLLM` starter:

- H100-focused hardware targeting,
- `Qwen 2.5 32B` defaults instead of a smaller starter model,
- long-context presets for premium deployments,
- the same small handler surface as the generic template.

## Positioning

This listing is for the higher-value end of the Hub:

- premium chat and assistant endpoints,
- heavier internal agents that need more headroom than 7B models,
- teams that want a deployable H100 default without building a worker from scratch.

The handler still forwards plain completions, chat completions, and explicit OpenAI-style routes through the local `vLLM` server inside the worker container.

## Presets

The Hub metadata ships with presets tuned for H100-class deployment:

- `Balanced 32B`
- `Long Context 32B`
- `High Throughput 32B`

The default model is:

- `Qwen/Qwen2.5-32B-Instruct`

## Important note about automated tests

The Hub submission smoke test intentionally uses a much smaller Qwen-family model than the default deployment model. That keeps automated validation fast and cheap while still proving the worker boots, serves requests, and routes payloads correctly.

User-facing deployment defaults in `.runpod/hub.json` remain centered on `Qwen/Qwen2.5-32B-Instruct`.

## Local verification

```bash
python -m unittest discover -s tests -v
python -m json.tool .runpod/hub.json
python -m json.tool .runpod/tests.json
python -m py_compile handler.py tests/test_handler.py
```

## Publish flow

1. Cut a GitHub release.
2. Submit the repo to RunPod Hub.
3. Let RunPod build and test the release.
4. Iterate by publishing new releases rather than rewriting old tags.
