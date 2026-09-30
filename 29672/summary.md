# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29672](https://github.com/ggml-org/llama.cpp/pull/29672) | ggml: add PTQ1_0, ternary at group 128 | 2026-09-29T17:18:16Z | @bri-prism |

## Target Info
- Primary: `PrismML-Eng_ptq1_0-base`
- Base: `PrismML-Eng_ptq1_0-base_base`
- Base checked out commit: `c85b92c69c955961621193cd51da194f3cbcedf3`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| PrismML-Eng_ptq1_0-base | N/A | N/A | N/A |
| PrismML-Eng_ptq1_0-base_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5097.62 | 5101.92 | 0.08% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5225.76 | 5225.06 | -0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4783.03 | 4762.43 | -0.43% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5028.39 | 5031.52 | 0.06% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.73 | 55.03 | -6.30% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 58.07 | 59.77 | 2.93% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5058.90 | 5025.77 | -0.65% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5179.80 | 5176.33 | -0.07% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4742.61 | 4727.09 | -0.33% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4983.63 | 4969.18 | -0.29% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 56.55 | 54.76 | -3.17% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.92 | 57.51 | 2.84% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1322.68 | 1301.04 | -1.64% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1334.37 | 1342.59 | 0.62% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1155.08 | 1158.47 | 0.29% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1282.44 | 1285.16 | 0.21% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.41 | 26.90 | -1.86% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.45 | 29.58 | 0.44% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### PrismML-Eng_ptq1_0-base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5225.06 ± 16.28 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5031.52 ± 5.96 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.77 ± 0.08 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5101.92 ± 36.70 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4762.43 ± 0.64 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.03 ± 0.31 |

build: c6413e3d5 (11257)
```

#### PrismML-Eng_ptq1_0-base_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5225.76 ± 16.58 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5028.39 ± 19.34 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.07 ± 0.50 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5097.62 ± 28.95 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4783.03 ± 2.28 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.73 ± 0.03 |

build: c85b92c69 (11256)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### PrismML-Eng_ptq1_0-base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5176.33 ± 16.89 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4969.18 ± 15.92 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.51 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5025.77 ± 85.11 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4727.09 ± 2.69 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.76 ± 0.81 |

build: c6413e3d5 (11257)
```

#### PrismML-Eng_ptq1_0-base_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5179.80 ± 18.37 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4983.63 ± 5.44 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.92 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5058.90 ± 29.71 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4742.61 ± 5.76 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.55 ± 0.02 |

build: c85b92c69 (11256)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### PrismML-Eng_ptq1_0-base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1342.59 ± 3.73 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1285.16 ± 2.97 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.58 ± 0.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1301.04 ± 2.30 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1158.47 ± 4.59 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.90 ± 0.00 |

build: c6413e3d5 (11257)
```

#### PrismML-Eng_ptq1_0-base_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1334.37 ± 5.68 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1282.44 ± 4.06 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.45 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1322.68 ± 2.00 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1155.08 ± 1.08 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.41 ± 0.01 |

build: c85b92c69 (11256)
```

- Bench data comparison: different
