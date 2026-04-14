# Qwen 2.5 32B H100 vLLM Worker

Deploy `Qwen/Qwen2.5-32B-Instruct` on RunPod Hub with an OpenAI-compatible `vLLM` worker tuned for H100-class serverless inference.

## Best for

- premium chat and assistant endpoints,
- internal agents that need more headroom than 7B models,
- users searching for a Qwen 32B, H100, or long-context `vLLM` worker.

## Request shapes

- `prompt` for `/v1/completions`
- `messages` for `/v1/chat/completions`
- `route` + `body` for explicit OpenAI-compatible requests

## Main knobs

- `MODEL_NAME`
- `MAX_MODEL_LEN`
- `GPU_MEMORY_UTILIZATION`
- `MAX_NUM_SEQS`
- `DEFAULT_MAX_TOKENS`
- `MAX_CONCURRENCY`

The smoke test uses a smaller Qwen model on easier-to-find GPU capacity, but the deployment presets stay centered on H100-class use.
