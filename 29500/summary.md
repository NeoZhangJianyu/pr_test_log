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
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp16384 | 0 | 4972.93 | 4955.32 | -0.35% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp16384 | 1 | 5277.97 | 5281.79 | 0.07% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 6018.50 | 6019.44 | 0.02% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 6129.90 | 6131.36 | 0.02% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 5499.61 | 5501.29 | 0.03% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5751.84 | 5752.61 | 0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 160.41 | 160.84 | 0.27% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 161.77 | 162.27 | 0.31% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp16384 | 0 | 4960.19 | 4962.16 | 0.04% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp16384 | 1 | 5264.07 | 5269.56 | 0.10% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 6006.82 | 5993.90 | -0.22% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 6108.37 | 6110.64 | 0.04% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 5480.39 | 5502.68 | 0.41% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 5735.77 | 5717.58 | -0.32% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 158.65 | 158.58 | -0.04% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 159.58 | 159.27 | -0.19% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp16384 | 0 | 1116.87 | 1116.51 | -0.03% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp16384 | 1 | 1340.81 | 1339.64 | -0.09% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1477.04 | 1474.21 | -0.19% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1517.46 | 1520.87 | 0.22% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1290.24 | 1290.32 | 0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1442.21 | 1444.74 | 0.18% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 56.13 | 56.20 | 0.12% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 57.63 | 57.54 | -0.16% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6131.36 ± 11.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5752.61 ± 15.21 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |      5281.79 ± 10.27 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.27 ± 0.20 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6019.44 ± 11.54 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      5501.29 ± 18.44 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |       4955.32 ± 9.98 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.84 ± 0.23 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6129.90 ± 10.75 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5751.84 ± 7.20 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |      5277.97 ± 17.86 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        161.77 ± 0.29 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6018.50 ± 16.43 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      5499.61 ± 22.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |       4972.93 ± 5.33 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.41 ± 0.10 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6110.64 ± 11.32 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5717.58 ± 18.32 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |       5269.56 ± 2.57 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        159.27 ± 0.16 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5993.90 ± 22.99 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       5502.68 ± 2.16 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |       4962.16 ± 3.12 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        158.58 ± 0.31 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       6108.37 ± 9.69 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       5735.77 ± 2.65 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |      5264.07 ± 10.97 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        159.58 ± 0.37 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6006.82 ± 23.18 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      5480.39 ± 18.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |       4960.19 ± 4.53 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        158.65 ± 0.72 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### clemenswasser_sycl-iq3s-multicol-mmvq (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1520.87 ± 6.95 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1444.74 ± 1.11 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |      1339.64 ± 14.89 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.54 ± 1.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1474.21 ± 5.70 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1290.32 ± 3.87 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |      1116.51 ± 14.85 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.20 ± 0.69 |

build: a75e09f41 (11201)
```

#### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1517.46 ± 6.77 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1442.21 ± 4.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |         pp16384 |      1340.81 ± 18.40 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.63 ± 1.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1477.04 ± 2.23 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1290.24 ± 3.09 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |         pp16384 |      1116.87 ± 16.70 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.13 ± 0.68 |

build: 81bc6b83f (11200)
```

- Bench data comparison: different
