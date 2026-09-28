# llama.cpp SYCL backend Test Log

## Logs

Log Table:

|PR|Created|Title|Author|Build|UT|Bench|Summary|
|-|-|-|-|-|-|-|-|
|[29510](https://github.com/ggml-org/llama.cpp/pull/29510)|2026-09-27T04:10:17Z|llama + CUDA: flash_attn_ext_rows (fix unified kv for multi-seq)|@am17an|Pass|Fail (N/A -> N/A)|Fail (Benchmark: Max -0.00%, Min -0.33%)|[summary.md](29510/summary.md)|
|[29507](https://github.com/ggml-org/llama.cpp/pull/29507)|2026-09-27T02:11:37Z|sycl: remove duplicate block-size defines from op headers|@Titaniumtown|Pass|Fail (N/A -> N/A)|Pass (Benchmark: Max 0.02%, Min -0.12%)|[summary.md](29507/summary.md)|
|[29506](https://github.com/ggml-org/llama.cpp/pull/29506)|2026-09-26T23:42:22Z|sycl: use ExternalProject to let this backend be built with SYCL compiler while everything else could use another|@a1batross|Pass|Fail (N/A -> N/A)|Fail (Benchmark: Max 0.09%, Min -0.65%)|[summary.md](29506/summary.md)|
|[29500](https://github.com/ggml-org/llama.cpp/pull/29500)|2026-09-26T21:50:03Z|sycl: add IQ3_S multi-column MMVQ|@clemenswasser|Pass|Fail (N/A -> N/A)|Pass (Qwen3.5-0.8B-MTP-Q4_K_M.gguf: Max 0.38%, Min -0.16%<br>Qwen3.5-0.8B-Q4_K_M.gguf: Max 1.06%, Min -0.07%<br>Qwen2-1.5Moe.Q4_K_M.gguf: Max 0.14%, Min 0.00%)|[summary.md](29500/summary.md)<br>Qwen3.5-0.8B-MTP-Q4_K_M.gguf<br>Qwen3.5-0.8B-Q4_K_M.gguf<br>Qwen2-1.5Moe.Q4_K_M.gguf|
