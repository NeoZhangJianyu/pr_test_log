# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29506](https://github.com/ggml-org/llama.cpp/pull/29506) | sycl: use ExternalProject to let this backend be built with SYCL compiler while everything else could use another | 2026-09-26T23:42:22Z | @a1batross |

## Target Info
- Primary: `a1batross_mix-rocm-sycl-build`
- Base: `a1batross_mix-rocm-sycl-build_base`
- Base checked out commit: `95887577ab5fead779581a7030a83c7752ff3234`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| a1batross_mix-rocm-sycl-build | N/A | N/A | N/A |
| a1batross_mix-rocm-sycl-build_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5106.41 | 4985.04 | -2.38% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5229.63 | 5101.34 | -2.45% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4778.90 | 4698.60 | -1.68% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5034.93 | 4909.04 | -2.50% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.51 | 56.81 | -2.91% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.30 | 54.62 | -7.89% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5068.69 | 5016.92 | -1.02% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5151.55 | 5150.39 | -0.02% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4575.92 | 4698.46 | 2.68% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4948.52 | 4932.73 | -0.32% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 53.24 | 55.81 | 4.83% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.69 | 57.23 | -0.80% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1306.30 | 1308.06 | 0.13% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1343.67 | 1344.04 | 0.03% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1157.20 | 1157.51 | 0.03% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1261.44 | 1285.50 | 1.91% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.24 | 27.32 | 0.29% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.61 | 29.61 | 0.00% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### a1batross_mix-rocm-sycl-build (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5101.34 ± 27.93 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4909.04 ± 18.46 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         54.62 ± 1.18 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4985.04 ± 25.22 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4698.60 ± 10.51 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.81 ± 0.17 |

build: 969134d94 (11207)
```

#### a1batross_mix-rocm-sycl-build_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5229.63 ± 16.41 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5034.93 ± 4.29 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.30 ± 0.57 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5106.41 ± 46.69 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4778.90 ± 0.42 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.51 ± 0.07 |

build: 95887577a (11205)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### a1batross_mix-rocm-sycl-build (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       5150.39 ± 9.67 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4932.73 ± 17.08 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.23 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5016.92 ± 21.03 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4698.46 ± 0.90 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.81 ± 0.06 |

build: 969134d94 (11207)
```

#### a1batross_mix-rocm-sycl-build_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5151.55 ± 16.56 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4948.52 ± 3.97 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.69 ± 0.04 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5068.69 ± 35.71 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4575.92 ± 90.96 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         53.24 ± 1.63 |

build: 95887577a (11205)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### a1batross_mix-rocm-sycl-build (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1344.04 ± 5.53 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1285.50 ± 2.90 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.61 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1308.06 ± 2.53 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1157.51 ± 1.21 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.32 ± 0.01 |

build: 969134d94 (11207)
```

#### a1batross_mix-rocm-sycl-build_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1343.67 ± 2.98 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      1261.44 ± 53.32 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.61 ± 0.00 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1306.30 ± 1.62 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1157.20 ± 1.97 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.24 ± 0.17 |

build: 95887577a (11205)
```

- Bench data comparison: different
