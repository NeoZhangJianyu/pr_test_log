# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29500](https://github.com/ggml-org/llama.cpp/pull/29500) | sycl: add IQ3_S multi-column MMVQ | 2026-09-26T21:50:03Z | @clemenswasser |

## Target Info
- Primary: `clemenswasser_sycl-iq3s-multicol-mmvq`
- Base: `clemenswasser_sycl-iq3s-multicol-mmvq_base`
- Base checked out commit: `81bc6b83f827df746eb129235488d325c49cae52`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| clemenswasser_sycl-iq3s-multicol-mmvq | N/A | N/A | N/A |
| clemenswasser_sycl-iq3s-multicol-mmvq_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 6020.95 | 6014.15 | -0.11% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 6123.43 | 6132.86 | 0.15% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 160.65 | 160.23 | -0.26% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 162.10 | 162.18 | 0.05% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 6005.22 | 6005.07 | -0.00% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 6099.28 | 6098.50 | -0.01% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 158.75 | 158.26 | -0.31% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 160.43 | 159.22 | -0.75% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1485.34 | 1485.18 | -0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1522.12 | 1523.30 | 0.08% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 56.77 | 56.80 | 0.05% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 59.01 | 58.87 | -0.24% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6132.86 ± 15.95 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.18 ± 0.85 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6014.15 ± 18.34 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.23 ± 0.16 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6123.43 ± 12.62 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.10 ± 0.75 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6020.95 ± 14.47 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.65 ± 0.37 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6098.50 ± 16.12 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        159.22 ± 0.50 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6005.07 ± 12.28 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        158.26 ± 0.27 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6099.28 ± 13.98 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        160.43 ± 0.39 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       6005.22 ± 9.28 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        158.75 ± 0.34 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1523.30 ± 7.61 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.87 ± 0.04 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1485.18 ± 1.48 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.80 ± 0.13 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1522.12 ± 6.60 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.01 ± 0.04 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1485.34 ± 1.22 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.77 ± 0.04 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different
