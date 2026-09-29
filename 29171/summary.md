# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29171](https://github.com/ggml-org/llama.cpp/pull/29171) | sycl: accelerate GLM MLA prefill with MKL flash attention | 2026-09-20T07:40:26Z | @anantshri |

## Target Info
- Primary: `anantshri_sycl-glm-mla-mkl-fa`
- Base: `anantshri_sycl-glm-mla-mkl-fa_base`
- Base checked out commit: `6e60f35608ec6918b44a9839c0c433687165f086`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| anantshri_sycl-glm-mla-mkl-fa | 18017 | 18039 | 99.88% |
| anantshri_sycl-glm-mla-mkl-fa_base | 18019 | 18039 | 99.89% |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5105.28 | 5100.51 | -0.09% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5227.55 | 5231.17 | 0.07% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4776.90 | 4766.12 | -0.23% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5041.43 | 5019.25 | -0.44% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 54.45 | 58.68 | 7.77% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 58.37 | 58.21 | -0.27% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5066.38 | 5058.68 | -0.15% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5185.50 | 5186.68 | 0.02% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4740.25 | 4732.17 | -0.17% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4981.34 | 4985.19 | 0.08% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.21 | 55.45 | 2.29% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.96 | 56.45 | 0.88% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1305.02 | 1304.72 | -0.02% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1335.83 | 1337.59 | 0.13% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1155.93 | 1152.28 | -0.32% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1282.22 | 1284.83 | 0.20% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.22 | 27.06 | -0.59% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.30 | 29.61 | 1.06% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### anantshri_sycl-glm-mla-mkl-fa (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5231.17 ± 19.93 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5019.25 ± 15.45 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.21 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5100.51 ± 24.91 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4766.12 ± 2.56 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.68 ± 0.06 |

build: 265f97481 (11150)
```

#### anantshri_sycl-glm-mla-mkl-fa_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5227.55 ± 16.58 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5041.43 ± 1.11 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.37 ± 0.85 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5105.28 ± 34.33 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4776.90 ± 0.98 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.45 ± 0.06 |

build: 6e60f3560 (11148)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### anantshri_sycl-glm-mla-mkl-fa (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5186.68 ± 18.38 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4985.19 ± 6.28 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.45 ± 0.76 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5058.68 ± 33.60 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4732.17 ± 1.50 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.45 ± 1.26 |

build: 265f97481 (11150)
```

#### anantshri_sycl-glm-mla-mkl-fa_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5185.50 ± 17.43 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4981.34 ± 11.60 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.96 ± 0.08 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5066.38 ± 29.72 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4740.25 ± 2.72 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.21 ± 0.10 |

build: 6e60f3560 (11148)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### anantshri_sycl-glm-mla-mkl-fa (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1337.59 ± 2.78 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1284.83 ± 4.80 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.61 ± 0.04 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1304.72 ± 3.25 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1152.28 ± 0.93 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.06 ± 0.22 |

build: 265f97481 (11150)
```

#### anantshri_sycl-glm-mla-mkl-fa_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1335.83 ± 3.78 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1282.22 ± 3.15 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.30 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1305.02 ± 2.33 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1155.93 ± 0.96 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.22 ± 0.00 |

build: 6e60f3560 (11148)
```

- Bench data comparison: different
