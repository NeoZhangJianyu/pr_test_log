# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29245](https://github.com/ggml-org/llama.cpp/pull/29245) | sycl: add grouped MoE XMX GEMM  | 2026-09-21T18:19:34Z | @cwriter |

## Target Info
- Primary: `cwriter_grouped_moe_xmx`
- Base: `cwriter_grouped_moe_xmx_base`
- Base checked out commit: `81bc6b83f827df746eb129235488d325c49cae52`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| cwriter_grouped_moe_xmx | N/A | N/A | N/A |
| cwriter_grouped_moe_xmx_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5055.43 | 5105.81 | 1.00% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5224.25 | 5227.03 | 0.05% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4759.60 | 4761.92 | 0.05% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5007.54 | 5028.54 | 0.42% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.38 | 58.72 | 0.58% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 57.84 | 58.90 | 1.83% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5024.25 | 5058.40 | 0.68% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5186.20 | 5184.54 | -0.03% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4744.70 | 4731.43 | -0.28% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4978.84 | 4985.40 | 0.13% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.83 | 56.45 | 2.95% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 56.48 | 57.72 | 2.20% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1316.96 | 1311.57 | -0.41% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1336.53 | 1339.19 | 0.20% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1156.61 | 1156.58 | -0.00% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1284.46 | 1281.74 | -0.21% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.01 | 26.87 | -0.52% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.56 | 29.55 | -0.03% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### cwriter_grouped_moe_xmx (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5227.03 ± 18.55 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5028.54 ± 7.46 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.90 ± 0.95 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5105.81 ± 34.22 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4761.92 ± 4.38 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.72 ± 0.07 |

build: 53095e0b7 (11202)
```

#### cwriter_grouped_moe_xmx_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5224.25 ± 20.02 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5007.54 ± 22.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.84 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5055.43 ± 71.40 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4759.60 ± 1.24 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.38 ± 0.08 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### cwriter_grouped_moe_xmx (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5184.54 ± 15.94 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4985.40 ± 7.20 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.72 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5058.40 ± 30.87 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4731.43 ± 0.99 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.45 ± 0.59 |

build: 53095e0b7 (11202)
```

#### cwriter_grouped_moe_xmx_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5186.20 ± 17.84 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4978.84 ± 8.07 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.48 ± 0.48 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5024.25 ± 71.73 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4744.70 ± 1.52 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.83 ± 1.06 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### cwriter_grouped_moe_xmx (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1339.19 ± 4.81 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1281.74 ± 2.96 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.55 ± 0.07 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1311.57 ± 3.52 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1156.58 ± 4.11 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.87 ± 0.01 |

build: 53095e0b7 (11202)
```

#### cwriter_grouped_moe_xmx_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1336.53 ± 5.51 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1284.46 ± 2.53 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.56 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1316.96 ± 5.08 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1156.61 ± 2.46 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.01 ± 0.17 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different
