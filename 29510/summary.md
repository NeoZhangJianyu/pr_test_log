# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29510](https://github.com/ggml-org/llama.cpp/pull/29510) | llama + CUDA: flash_attn_ext_rows (fix unified kv for multi-seq) | 2026-09-27T04:10:17Z | @am17an |

## Target Info
- Primary: `ggml-org_aman-sparse-unified`
- Base: `ggml-org_aman-sparse-unified_base`
- Base checked out commit: `85ca3b52c33f5477f75985a251543f5f73010e8a`
- GGUF file: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: |
| ggml-org_aman-sparse-unified | N/A | N/A | N/A |
| ggml-org_aman-sparse-unified_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | ---: | ---: | ---: | ---: |
| pp512 | 0 | 6011.01 | 6010.96 | -0.00% |
| pp512 | 1 | 6129.29 | 6124.08 | -0.09% |
| tg128 | 0 | 160.50 | 160.27 | -0.14% |
| tg128 | 1 | 161.76 | 161.23 | -0.33% |

## Bench Results

### ggml-org_aman-sparse-unified (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6124.08 ± 24.87 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        161.23 ± 0.41 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6010.96 ± 14.03 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.27 ± 0.17 |

build: 7908e9e8c (11209)
```

### ggml-org_aman-sparse-unified_base (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6129.29 ± 17.18 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        161.76 ± 0.14 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6011.01 ± 14.21 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.50 ± 0.16 |

build: 85ca3b52c (11208)
```

- Bench data comparison from bench.log: different
