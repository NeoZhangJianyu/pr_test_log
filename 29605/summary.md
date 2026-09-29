# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29605](https://github.com/ggml-org/llama.cpp/pull/29605) | sycl: FWHT optimizations | 2026-09-28T18:45:59Z | @bri-prism |

## Target Info
- Primary: `PrismML-Eng_sycl-fwht-f16`
- Base: `PrismML-Eng_sycl-fwht-f16_base`
- Base checked out commit: `f1ea206218210afb913ae2f5d2c51faed35915da`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| PrismML-Eng_sycl-fwht-f16 | N/A | N/A | N/A |
| PrismML-Eng_sycl-fwht-f16_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5043.85 | 5089.50 | 0.91% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5221.78 | 5223.99 | 0.04% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4774.12 | 4756.29 | -0.37% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5020.24 | 5017.70 | -0.05% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 54.76 | 58.52 | 6.87% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 58.81 | 59.80 | 1.68% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5038.33 | 5038.91 | 0.01% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5183.57 | 5185.24 | 0.03% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4744.12 | 4733.65 | -0.22% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4990.40 | 4984.40 | -0.12% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 56.67 | 56.60 | -0.12% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.75 | 56.12 | -2.82% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1322.18 | 1303.29 | -1.43% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1349.85 | 1338.65 | -0.83% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1166.81 | 1153.30 | -1.16% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1284.43 | 1283.92 | -0.04% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.28 | 27.34 | 0.22% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.51 | 29.61 | 0.34% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### PrismML-Eng_sycl-fwht-f16 (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5223.99 ± 18.17 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5017.70 ± 18.69 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.80 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5089.50 ± 38.34 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4756.29 ± 0.56 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.52 ± 0.10 |

build: 21fa2db9f (11237)
```

#### PrismML-Eng_sycl-fwht-f16_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5221.78 ± 16.74 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5020.24 ± 20.20 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.81 ± 1.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5043.85 ± 88.60 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4774.12 ± 1.26 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.76 ± 0.06 |

build: f1ea20621 (11236)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### PrismML-Eng_sycl-fwht-f16 (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5185.24 ± 15.75 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4984.40 ± 4.26 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.12 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5038.91 ± 32.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4733.65 ± 2.10 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.60 ± 0.04 |

build: 21fa2db9f (11237)
```

#### PrismML-Eng_sycl-fwht-f16_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5183.57 ± 15.19 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4990.40 ± 5.44 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.75 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5038.33 ± 26.42 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4744.12 ± 2.33 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.67 ± 0.04 |

build: f1ea20621 (11236)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### PrismML-Eng_sycl-fwht-f16 (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1338.65 ± 4.82 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1283.92 ± 4.74 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.61 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1303.29 ± 2.39 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1153.30 ± 3.70 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.34 ± 0.01 |

build: 21fa2db9f (11237)
```

#### PrismML-Eng_sycl-fwht-f16_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1349.85 ± 5.46 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1284.43 ± 5.62 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.51 ± 0.10 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1322.18 ± 1.61 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1166.81 ± 0.93 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.28 ± 0.19 |

build: f1ea20621 (11236)
```

- Bench data comparison: different
