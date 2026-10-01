# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29696](https://github.com/ggml-org/llama.cpp/pull/29696) | sycl: wide stores and 256-thread groups for the q4_K/q5_K weight dequant | 2026-09-30T05:19:00Z | @Titaniumtown |

## Target Info
- Primary: `Titaniumtown_pr-sycl-dequant-wide-stores`
- Base: `Titaniumtown_pr-sycl-dequant-wide-stores_base`
- Base checked out commit: `fc07d781e61f0d23764394e902b88d26a974e202`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) Pro B70 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| Titaniumtown_pr-sycl-dequant-wide-stores | N/A | N/A | N/A |
| Titaniumtown_pr-sycl-dequant-wide-stores_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 11641.49 | 11679.90 | 0.33% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 12257.14 | 11734.39 | -4.26% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 10340.59 | 10363.90 | 0.23% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 11748.58 | 11291.05 | -3.89% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 345.58 | 346.15 | 0.16% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 358.00 | 360.17 | 0.61% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 11642.04 | 11650.19 | 0.07% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 12222.38 | 11637.52 | -4.79% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 10336.92 | 10353.73 | 0.16% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 11730.87 | 11191.22 | -4.60% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 355.20 | 354.62 | -0.16% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 372.14 | 371.44 | -0.19% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 2170.77 | 2198.26 | 1.27% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 2252.09 | 2052.41 | -8.87% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1861.83 | 1875.34 | 0.73% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 2158.86 | 1972.40 | -8.64% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 133.51 | 133.96 | 0.34% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 137.11 | 136.77 | -0.25% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### Titaniumtown_pr-sycl-dequant-wide-stores (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     11734.39 ± 20.67 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11291.05 ± 6.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        360.17 ± 0.40 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11679.90 ± 38.57 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10363.90 ± 1.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        346.15 ± 0.55 |

build: 137910fda (11244)
```

#### Titaniumtown_pr-sycl-dequant-wide-stores_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     12257.14 ± 14.01 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11748.58 ± 2.62 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        358.00 ± 0.50 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11641.49 ± 32.29 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10340.59 ± 6.31 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        345.58 ± 0.37 |

build: fc07d781e (11243)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### Titaniumtown_pr-sycl-dequant-wide-stores (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     11637.52 ± 24.42 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11191.22 ± 3.99 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        371.44 ± 0.76 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11650.19 ± 61.53 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10353.73 ± 5.94 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        354.62 ± 0.72 |

build: 137910fda (11244)
```

#### Titaniumtown_pr-sycl-dequant-wide-stores_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     12222.38 ± 13.18 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11730.87 ± 8.38 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        372.14 ± 0.68 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11642.04 ± 51.23 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10336.92 ± 4.16 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        355.20 ± 0.46 |

build: fc07d781e (11243)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### Titaniumtown_pr-sycl-dequant-wide-stores (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       2052.41 ± 7.29 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1972.40 ± 5.28 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        136.77 ± 0.39 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       2198.26 ± 2.59 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1875.34 ± 4.90 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        133.96 ± 0.08 |

build: 137910fda (11244)
```

#### Titaniumtown_pr-sycl-dequant-wide-stores_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      2252.09 ± 15.94 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       2158.86 ± 5.48 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        137.11 ± 0.39 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       2170.77 ± 1.51 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1861.83 ± 3.87 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        133.51 ± 0.08 |

build: fc07d781e (11243)
```

- Bench data comparison: different
