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
- GPU: `13th Gen Intel(R) Core(TM) i7-13700K`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| clemenswasser_sycl-iq3s-multicol-mmvq | N/A | N/A | N/A |
| clemenswasser_sycl-iq3s-multicol-mmvq_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 6015.86 | 6006.08 | -0.16% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 6131.30 | 6130.87 | -0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 160.52 | 160.77 | 0.16% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 161.57 | 162.19 | 0.38% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 6001.38 | 5997.03 | -0.07% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 6098.20 | 6103.81 | 0.09% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 158.72 | 159.62 | 0.57% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 159.08 | 160.77 | 1.06% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1484.04 | 1484.16 | 0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1523.41 | 1524.37 | 0.06% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 56.82 | 56.90 | 0.14% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 58.93 | 58.93 | 0.00% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6130.87 ± 17.77 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.19 ± 0.66 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6006.08 ± 17.81 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.77 ± 0.46 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6131.30 ± 18.09 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        161.57 ± 0.22 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6015.86 ± 20.25 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.52 ± 0.07 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       6103.81 ± 8.54 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        160.77 ± 0.04 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5997.03 ± 20.68 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        159.62 ± 0.03 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6098.20 ± 11.92 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        159.08 ± 0.17 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6001.38 ± 15.61 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        158.72 ± 0.59 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1524.37 ± 6.95 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.93 ± 0.08 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1484.16 ± 2.63 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.90 ± 0.07 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1523.41 ± 6.35 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.93 ± 0.07 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1484.04 ± 1.31 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.82 ± 0.05 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different
