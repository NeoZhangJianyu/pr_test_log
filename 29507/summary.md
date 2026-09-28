# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29507](https://github.com/ggml-org/llama.cpp/pull/29507) | sycl: remove duplicate block-size defines from op headers | 2026-09-27T02:11:37Z | @Titaniumtown |

## Target Info
- Primary: `Titaniumtown_pr-blockdup`
- Base: `Titaniumtown_pr-blockdup_base`
- Base checked out commit: `08618ff8e735141d8e4e5be28e6d6af170e4757b`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| Titaniumtown_pr-blockdup | N/A | N/A | N/A |
| Titaniumtown_pr-blockdup_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5051.55 | 5104.00 | 1.04% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5224.69 | 5224.56 | -0.00% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4781.90 | 4780.19 | -0.04% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5028.31 | 5029.02 | 0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 56.24 | 58.65 | 4.29% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.86 | 59.76 | -0.17% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5049.87 | 5054.19 | 0.09% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5176.20 | 5180.63 | 0.09% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4745.84 | 4738.12 | -0.16% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4993.70 | 4984.82 | -0.18% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.34 | 54.41 | 0.13% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.65 | 56.55 | -1.91% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1321.20 | 1321.12 | -0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1348.28 | 1341.73 | -0.49% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1157.34 | 1165.01 | 0.66% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1288.34 | 1287.01 | -0.10% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 26.98 | 26.88 | -0.37% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.59 | 29.45 | -0.47% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### Titaniumtown_pr-blockdup (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5224.56 ± 19.36 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5029.02 ± 22.52 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.76 ± 0.04 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5104.00 ± 32.88 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4780.19 ± 3.32 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.65 ± 0.05 |

build: a2b724c44 (11199)
```

#### Titaniumtown_pr-blockdup_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5224.69 ± 15.57 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5028.31 ± 20.35 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.86 ± 0.08 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5051.55 ± 71.77 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4781.90 ± 1.25 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.24 ± 2.18 |

build: 08618ff8e (11198)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### Titaniumtown_pr-blockdup (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5180.63 ± 17.77 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4984.82 ± 12.24 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.55 ± 0.75 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5054.19 ± 29.02 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4738.12 ± 6.09 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.41 ± 0.03 |

build: a2b724c44 (11199)
```

#### Titaniumtown_pr-blockdup_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5176.20 ± 16.52 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4993.70 ± 4.50 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.65 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5049.87 ± 24.73 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4745.84 ± 0.28 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.34 ± 0.04 |

build: 08618ff8e (11198)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### Titaniumtown_pr-blockdup (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1341.73 ± 4.63 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1287.01 ± 2.07 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.45 ± 0.07 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1321.12 ± 2.14 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1165.01 ± 0.96 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.88 ± 0.01 |

build: a2b724c44 (11199)
```

#### Titaniumtown_pr-blockdup_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1348.28 ± 3.48 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1288.34 ± 2.35 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.59 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1321.20 ± 1.95 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1157.34 ± 1.05 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.98 ± 0.18 |

build: 08618ff8e (11198)
```

- Bench data comparison: different
