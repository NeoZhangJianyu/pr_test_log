# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29107](https://github.com/ggml-org/llama.cpp/pull/29107) | sycl: IQ3 code reorder | 2026-09-18T21:35:09Z | @anantshri |

## Target Info
- Primary: `anantshri_sycl-b70-iq3`
- Base: `anantshri_sycl-b70-iq3_base`
- Base checked out commit: `d7fb90e8e2494b2908934d956a3202fd60152ee0`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) Pro B70 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| anantshri_sycl-b70-iq3 | N/A | N/A | N/A |
| anantshri_sycl-b70-iq3_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 11640.15 | 11697.53 | 0.49% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 12267.87 | 11976.80 | -2.37% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 10341.34 | 10364.85 | 0.23% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 11751.06 | 11769.60 | 0.16% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 345.63 | 346.01 | 0.11% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 360.64 | 359.88 | -0.21% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 11669.27 | 11680.63 | 0.10% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 12235.75 | 12246.76 | 0.09% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 10345.70 | 10379.01 | 0.32% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 11748.22 | 11768.09 | 0.17% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 354.77 | 354.46 | -0.09% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 371.67 | 371.59 | -0.02% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 2171.19 | 2198.51 | 1.26% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 2255.53 | 2262.70 | 0.32% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1864.88 | 1876.93 | 0.65% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 2160.36 | 2170.93 | 0.49% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 133.73 | 133.99 | 0.19% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 137.07 | 136.23 | -0.61% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### anantshri_sycl-b70-iq3 (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |    11976.80 ± 708.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11769.60 ± 5.08 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        359.88 ± 0.51 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11697.53 ± 36.43 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10364.85 ± 1.24 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        346.01 ± 0.29 |

build: 9748c5b34 (11212)
```

#### anantshri_sycl-b70-iq3_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     12267.87 ± 15.22 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11751.06 ± 8.48 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        360.64 ± 0.44 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11640.15 ± 45.96 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10341.34 ± 7.13 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        345.63 ± 0.57 |

build: d7fb90e8e (11211)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### anantshri_sycl-b70-iq3 (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     12246.76 ± 20.56 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11768.09 ± 4.62 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        371.59 ± 0.69 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11680.63 ± 37.45 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10379.01 ± 4.97 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        354.46 ± 0.59 |

build: 9748c5b34 (11212)
```

#### anantshri_sycl-b70-iq3_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     12235.75 ± 12.73 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      11748.22 ± 7.97 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        371.67 ± 0.80 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |     11669.27 ± 35.78 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      10345.70 ± 8.21 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        354.77 ± 0.38 |

build: d7fb90e8e (11211)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### anantshri_sycl-b70-iq3 (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       2262.70 ± 1.12 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       2170.93 ± 7.17 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        136.23 ± 0.34 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       2198.51 ± 1.78 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1876.93 ± 4.63 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        133.99 ± 0.03 |

build: 9748c5b34 (11212)
```

#### anantshri_sycl-b70-iq3_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      2255.53 ± 12.94 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       2160.36 ± 5.14 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        137.07 ± 0.35 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       2171.19 ± 0.81 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1864.88 ± 2.56 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        133.73 ± 0.07 |

build: d7fb90e8e (11211)
```

- Bench data comparison: different
