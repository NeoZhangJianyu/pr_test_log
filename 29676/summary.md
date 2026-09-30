# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29676](https://github.com/ggml-org/llama.cpp/pull/29676) | cuda: add PTQ1_0 support | 2026-09-29T19:41:47Z | @bri-prism |

## Target Info
- Primary: `PrismML-Eng_ptq1_0-cuda`
- Base: `PrismML-Eng_ptq1_0-cuda_base`
- Base checked out commit: `c85b92c69c955961621193cd51da194f3cbcedf3`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| PrismML-Eng_ptq1_0-cuda | N/A | N/A | N/A |
| PrismML-Eng_ptq1_0-cuda_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5067.29 | 5105.22 | 0.75% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5229.68 | 5221.78 | -0.15% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4762.54 | 4773.44 | 0.23% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5030.81 | 5022.22 | -0.17% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.51 | 55.32 | -5.45% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.82 | 59.79 | -0.05% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5053.29 | 5058.84 | 0.11% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5183.24 | 5179.41 | -0.07% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4734.92 | 4746.88 | 0.25% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4985.92 | 4982.93 | -0.06% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.31 | 56.79 | 4.57% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.66 | 57.67 | 0.02% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1299.49 | 1323.80 | 1.87% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1337.75 | 1337.40 | -0.03% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1154.56 | 1167.16 | 1.09% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1284.48 | 1288.79 | 0.34% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 26.92 | 26.89 | -0.11% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.65 | 29.37 | -0.94% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### PrismML-Eng_ptq1_0-cuda (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5221.78 ± 21.82 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5022.22 ± 17.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.79 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5105.22 ± 36.01 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4773.44 ± 6.01 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.32 ± 1.43 |

build: 82c9c221f (11258)
```

#### PrismML-Eng_ptq1_0-cuda_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5229.68 ± 18.45 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5030.81 ± 5.53 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.82 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5067.29 ± 94.28 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4762.54 ± 4.01 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.51 ± 0.05 |

build: c85b92c69 (11256)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### PrismML-Eng_ptq1_0-cuda (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5179.41 ± 19.59 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4982.93 ± 15.28 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.67 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5058.84 ± 30.86 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4746.88 ± 1.47 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.79 ± 0.01 |

build: 82c9c221f (11258)
```

#### PrismML-Eng_ptq1_0-cuda_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5183.24 ± 14.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4985.92 ± 6.29 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.66 ± 0.30 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5053.29 ± 25.86 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4734.92 ± 4.29 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.31 ± 0.03 |

build: c85b92c69 (11256)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### PrismML-Eng_ptq1_0-cuda (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1337.40 ± 2.83 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1288.79 ± 8.55 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.37 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1323.80 ± 2.75 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1167.16 ± 2.15 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.89 ± 0.01 |

build: 82c9c221f (11258)
```

#### PrismML-Eng_ptq1_0-cuda_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1337.75 ± 2.91 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1284.48 ± 1.87 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.65 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1299.49 ± 3.68 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1154.56 ± 1.30 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.92 ± 0.03 |

build: c85b92c69 (11256)
```

- Bench data comparison: different
