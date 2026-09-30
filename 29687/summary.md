# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29687](https://github.com/ggml-org/llama.cpp/pull/29687) | sycl: fuse the delta-net alpha gate (add + unary + mul) | 2026-09-30T02:26:51Z | @Titaniumtown |

## Target Info
- Primary: `Titaniumtown_pr-sycl-add-unary-mul`
- Base: `Titaniumtown_pr-sycl-add-unary-mul_base`
- Base checked out commit: `fc07d781e61f0d23764394e902b88d26a974e202`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| Titaniumtown_pr-sycl-add-unary-mul | N/A | N/A | N/A |
| Titaniumtown_pr-sycl-add-unary-mul_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5085.13 | 5127.35 | 0.83% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5201.47 | 5271.61 | 1.35% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4768.24 | 4821.42 | 1.12% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5019.76 | 5064.95 | 0.90% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.56 | 60.31 | 2.99% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.76 | 61.39 | 2.73% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5054.68 | 5090.93 | 0.72% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5185.64 | 5223.16 | 0.72% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4732.05 | 4780.15 | 1.02% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4982.33 | 5018.25 | 0.72% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 56.75 | 55.98 | -1.36% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.66 | 58.81 | 1.99% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1307.56 | 1307.38 | -0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1337.34 | 1352.17 | 1.11% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1153.60 | 1155.79 | 0.19% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1279.24 | 1289.92 | 0.83% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.25 | 27.27 | 0.07% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.48 | 29.52 | 0.14% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### Titaniumtown_pr-sycl-add-unary-mul (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5271.61 ± 17.09 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5064.95 ± 20.91 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         61.39 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5127.35 ± 89.01 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4821.42 ± 0.43 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         60.31 ± 0.06 |

build: 4ec8ac18d (11246)
```

#### Titaniumtown_pr-sycl-add-unary-mul_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5201.47 ± 52.71 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5019.76 ± 15.93 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.76 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5085.13 ± 24.27 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4768.24 ± 4.86 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.56 ± 0.03 |

build: fc07d781e (11243)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### Titaniumtown_pr-sycl-add-unary-mul (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5223.16 ± 16.04 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5018.25 ± 15.80 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.81 ± 0.02 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5090.93 ± 40.20 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4780.15 ± 1.20 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.98 ± 1.12 |

build: 4ec8ac18d (11246)
```

#### Titaniumtown_pr-sycl-add-unary-mul_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5185.64 ± 13.49 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4982.33 ± 4.90 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.66 ± 0.04 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5054.68 ± 32.51 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4732.05 ± 1.17 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.75 ± 0.07 |

build: fc07d781e (11243)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### Titaniumtown_pr-sycl-add-unary-mul (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1352.17 ± 2.78 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1289.92 ± 3.76 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.52 ± 0.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1307.38 ± 1.61 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1155.79 ± 1.60 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.27 ± 0.00 |

build: 4ec8ac18d (11246)
```

#### Titaniumtown_pr-sycl-add-unary-mul_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1337.34 ± 4.54 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1279.24 ± 2.44 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.48 ± 0.10 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1307.56 ± 1.75 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1153.60 ± 2.36 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.25 ± 0.00 |

build: fc07d781e (11243)
```

- Bench data comparison: different
