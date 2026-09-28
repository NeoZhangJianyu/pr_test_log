# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29510](https://github.com/ggml-org/llama.cpp/pull/29510) | llama + CUDA: flash_attn_ext_rows (fix unified kv for multi-seq) | 2026-09-27T04:10:17Z | @am17an |

## Target Info
- Primary: `ggml-org_aman-sparse-unified`
- Base: `ggml-org_aman-sparse-unified_base`
- Base checked out commit: `85ca3b52c33f5477f75985a251543f5f73010e8a`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| ggml-org_aman-sparse-unified | N/A | N/A | N/A |
| ggml-org_aman-sparse-unified_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp16384 | 0 | 4251.40 | 4280.45 | 0.68% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp16384 | 1 | 4640.09 | 4647.29 | 0.16% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5101.70 | 5077.55 | -0.47% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5222.04 | 5213.31 | -0.17% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4763.22 | 4762.31 | -0.02% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5018.10 | 5024.06 | 0.12% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.66 | 56.65 | -3.43% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.68 | 59.49 | -0.32% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp16384 | 0 | 4223.09 | 4256.81 | 0.80% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp16384 | 1 | 4598.64 | 4610.36 | 0.25% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5059.11 | 5043.70 | -0.30% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5159.61 | 5174.51 | 0.29% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4723.14 | 4744.01 | 0.44% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4975.39 | 4983.69 | 0.17% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 56.43 | 56.63 | 0.35% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.09 | 57.64 | 0.96% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp16384 | 0 | 1018.43 | 1020.99 | 0.25% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp16384 | 1 | 1193.55 | 1209.65 | 1.35% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1302.93 | 1323.39 | 1.57% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1338.81 | 1348.05 | 0.69% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1151.99 | 1159.80 | 0.68% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1279.54 | 1282.09 | 0.20% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 26.97 | 26.86 | -0.41% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.11 | 29.44 | 1.13% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### ggml-org_aman-sparse-unified (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5213.31 ± 24.56 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5024.06 ± 16.64 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |       4647.29 ± 4.68 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.49 ± 0.77 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5077.55 ± 41.50 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4762.31 ± 14.96 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |       4280.45 ± 2.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.65 ± 1.95 |

build: 7908e9e8c (11209)
```

#### ggml-org_aman-sparse-unified_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5222.04 ± 15.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5018.10 ± 17.69 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |       4640.09 ± 4.04 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.68 ± 0.08 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5101.70 ± 39.19 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4763.22 ± 0.98 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |      4251.40 ± 12.90 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.66 ± 0.11 |

build: 85ca3b52c (11208)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### ggml-org_aman-sparse-unified (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5174.51 ± 18.26 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4983.69 ± 14.98 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |       4610.36 ± 3.27 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.64 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5043.70 ± 29.56 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4744.01 ± 1.15 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |       4256.81 ± 5.57 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.63 ± 0.07 |

build: 7908e9e8c (11209)
```

#### ggml-org_aman-sparse-unified_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5159.61 ± 14.03 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4975.39 ± 5.11 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |       4598.64 ± 3.24 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.09 ± 0.52 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5059.11 ± 41.77 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4723.14 ± 3.04 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |      4223.09 ± 15.39 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.43 ± 0.05 |

build: 85ca3b52c (11208)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### ggml-org_aman-sparse-unified (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      1348.05 ± 14.65 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1282.09 ± 4.15 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |       1209.65 ± 8.31 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.44 ± 0.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1323.39 ± 0.96 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1159.80 ± 3.34 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |      1020.99 ± 10.81 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.86 ± 0.11 |

build: 7908e9e8c (11209)
```

#### ggml-org_aman-sparse-unified_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1338.81 ± 1.66 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1279.54 ± 2.26 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |      1193.55 ± 17.67 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.11 ± 0.40 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1302.93 ± 1.22 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1151.99 ± 0.66 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |      1018.43 ± 10.09 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.97 ± 0.21 |

build: 85ca3b52c (11208)
```

- Bench data comparison: different
