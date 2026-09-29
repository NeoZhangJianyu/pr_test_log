# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29375](https://github.com/ggml-org/llama.cpp/pull/29375) | sycl : Q5_K reorder-layout MMVQ and fused GLU | 2026-09-24T13:34:28Z | @NickM-27 |

## Target Info
- Primary: `NickM-27_sycl-q5k-mmvq`
- Base: `NickM-27_sycl-q5k-mmvq_base`
- Base checked out commit: `6b790a9c291b5d7af3312bbf9f0c558aa023b13e`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| NickM-27_sycl-q5k-mmvq | N/A | N/A | N/A |
| NickM-27_sycl-q5k-mmvq_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5111.07 | 5078.53 | -0.64% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5231.84 | 5233.22 | 0.03% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4765.37 | 4767.66 | 0.05% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5036.51 | 5029.42 | -0.14% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.51 | 54.57 | -6.73% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 59.85 | 60.09 | 0.40% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5068.42 | 5060.53 | -0.16% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5175.39 | 5182.09 | 0.13% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4731.91 | 4740.73 | 0.19% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4983.24 | 4973.34 | -0.20% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.37 | 56.78 | 4.43% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 56.00 | 57.84 | 3.29% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1304.37 | 1322.08 | 1.36% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1334.69 | 1345.98 | 0.85% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1152.48 | 1163.15 | 0.93% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1280.87 | 1288.07 | 0.56% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 26.93 | 27.43 | 1.86% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.60 | 29.56 | -0.14% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### NickM-27_sycl-q5k-mmvq (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5233.22 ± 19.49 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5029.42 ± 20.62 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         60.09 ± 0.10 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5078.53 ± 88.39 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4767.66 ± 17.92 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.57 ± 0.05 |

build: d696e51ca (11163)
```

#### NickM-27_sycl-q5k-mmvq_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5231.84 ± 14.15 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5036.51 ± 3.47 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.85 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5111.07 ± 45.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4765.37 ± 0.82 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.51 ± 0.06 |

build: 6b790a9c2 (11159)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### NickM-27_sycl-q5k-mmvq (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5182.09 ± 20.91 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4973.34 ± 21.95 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.84 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5060.53 ± 30.40 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4740.73 ± 3.40 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.78 ± 0.02 |

build: d696e51ca (11163)
```

#### NickM-27_sycl-q5k-mmvq_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5175.39 ± 16.10 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4983.24 ± 2.10 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.00 ± 0.15 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5068.42 ± 29.68 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4731.91 ± 2.12 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.37 ± 2.43 |

build: 6b790a9c2 (11159)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### NickM-27_sycl-q5k-mmvq (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1345.98 ± 6.07 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1288.07 ± 3.19 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.56 ± 0.09 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1322.08 ± 2.34 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1163.15 ± 4.31 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.43 ± 0.01 |

build: d696e51ca (11163)
```

#### NickM-27_sycl-q5k-mmvq_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1334.69 ± 6.34 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1280.87 ± 5.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.60 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1304.37 ± 1.19 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1152.48 ± 1.33 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.93 ± 0.01 |

build: 6b790a9c2 (11159)
```

- Bench data comparison: different
