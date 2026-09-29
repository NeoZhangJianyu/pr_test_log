# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29459](https://github.com/ggml-org/llama.cpp/pull/29459) | sycl : add a work-around for Level Zero crash/hang | 2026-09-26T04:27:07Z | @stolk |

## Target Info
- Primary: `stolk_sycl-comm-direct-alloc`
- Base: `stolk_sycl-comm-direct-alloc_base`
- Base checked out commit: `1ab7e5ad2d4e7295c94c3b966a3e0b70fa365865`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| stolk_sycl-comm-direct-alloc | N/A | N/A | N/A |
| stolk_sycl-comm-direct-alloc_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5085.22 | 4718.87 | -7.20% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5225.66 | 5224.12 | -0.03% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4781.90 | 4489.34 | -6.12% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5036.66 | 5024.14 | -0.25% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.90 | 26.50 | -55.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.99 | 30.60 | -48.99% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5041.15 | 4879.26 | -3.21% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5181.08 | 4822.04 | -6.93% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4561.84 | 4600.98 | 0.86% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4991.18 | 4720.57 | -5.42% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 26.77 | 51.46 | 92.23% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.53 | 50.45 | -12.31% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1262.28 | 1307.74 | 3.60% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1259.49 | 1336.92 | 6.15% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1160.90 | 1160.94 | 0.00% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1198.57 | 1282.63 | 7.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.23 | 27.12 | -0.40% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 19.23 | 29.41 | 52.94% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### stolk_sycl-comm-direct-alloc (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5224.12 ± 19.03 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5024.14 ± 19.95 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         30.60 ± 0.75 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4718.87 ± 28.13 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4489.34 ± 30.22 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.50 ± 1.48 |

build: 1eadf9f6c (11178)
```

#### stolk_sycl-comm-direct-alloc_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5225.66 ± 17.65 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5036.66 ± 20.98 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.99 ± 0.09 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5085.22 ± 32.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4781.90 ± 1.27 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.90 ± 0.05 |

build: 1ab7e5ad2 (11177)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### stolk_sycl-comm-direct-alloc (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       4822.04 ± 6.32 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4720.57 ± 25.53 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         50.45 ± 1.50 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4879.26 ± 51.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4600.98 ± 15.53 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         51.46 ± 1.08 |

build: 1eadf9f6c (11178)
```

#### stolk_sycl-comm-direct-alloc_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5181.08 ± 16.38 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4991.18 ± 5.44 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.53 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5041.15 ± 26.57 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4561.84 ± 10.01 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.77 ± 1.45 |

build: 1ab7e5ad2 (11177)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### stolk_sycl-comm-direct-alloc (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1336.92 ± 1.22 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1282.63 ± 3.04 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.41 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1307.74 ± 6.93 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1160.94 ± 3.04 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.12 ± 0.01 |

build: 1eadf9f6c (11178)
```

#### stolk_sycl-comm-direct-alloc_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      1259.49 ± 14.15 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      1198.57 ± 10.21 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         19.23 ± 0.69 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1262.28 ± 4.48 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1160.90 ± 2.30 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.23 ± 0.02 |

build: 1ab7e5ad2 (11177)
```

- Bench data comparison: different
