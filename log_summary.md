# llama.cpp SYCL backend Test Log

## Logs

Log Table:

|PR|Created|Build|UT|Bench|Summary|Title|Author|
|-|-|-|-|-|-|-|-|
|[29510](https://github.com/ggml-org/llama.cpp/pull/29510)|2026-09-27T04:10:17Z|Pass|Fail (N/A -> N/A)|Pass<br> (Qwen3.5-0.8B-MTP-Q4_K_M.gguf: Max 0.68%, Min -3.43%<br>Qwen3.5-0.8B-Q4_K_M.gguf: Max 0.96%, Min -0.30%<br>Qwen2-1.5Moe.Q4_K_M.gguf: Max 1.57%, Min -0.41%)|[summary.md](29510/summary.md)|llama + CUDA: flash_attn_ext_rows (fix unified kv for multi-seq)|@am17an|
|[29500](https://github.com/ggml-org/llama.cpp/pull/29500)|2026-09-26T21:50:03Z|Pass|Fail (N/A -> N/A)|Pass<br> (Qwen3.5-0.8B-MTP-Q4_K_M.gguf: Max 0.31%, Min -0.35%<br>Qwen3.5-0.8B-Q4_K_M.gguf: Max 0.41%, Min -0.32%<br>Qwen2-1.5Moe.Q4_K_M.gguf: Max 0.22%, Min -0.19%)|[summary.md](29500/summary.md)|sycl: add IQ3_S multi-column MMVQ|@clemenswasser|
