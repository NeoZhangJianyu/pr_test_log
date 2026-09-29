# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29186](https://github.com/ggml-org/llama.cpp/pull/29186) | SYCL: Q8_0 DMMV ESIMD and MMVQ wide load | 2026-09-20T19:32:58Z | @cwriter |

## Target Info
- Primary: `cwriter_wide_load_and_esimd`
- Base: `cwriter_wide_load_and_esimd_base`
- Base checked out commit: `c9064dded732d81f90b34e6b33d4fbd77cbfa058`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| cwriter_wide_load_and_esimd | N/A | N/A | N/A |
| cwriter_wide_load_and_esimd_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5082.94 | 5105.47 | 0.44% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5224.20 | 5166.26 | -1.11% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4765.83 | 4756.70 | -0.19% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5024.52 | 5026.41 | 0.04% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 55.81 | 55.28 | -0.95% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 57.75 | 59.67 | 3.32% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5049.54 | 5075.56 | 0.52% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5179.15 | 5183.46 | 0.08% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4742.62 | 4730.37 | -0.26% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4989.43 | 4970.84 | -0.37% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.30 | 57.19 | 5.32% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.99 | 58.93 | 5.25% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1306.85 | 1310.69 | 0.29% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1341.06 | 1340.98 | -0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1156.96 | 1153.30 | -0.32% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1290.10 | 1280.94 | -0.71% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.07 | 26.89 | -0.66% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.66 | 29.41 | -0.84% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### cwriter_wide_load_and_esimd (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |     5166.26 ± 144.43 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5026.41 ± 18.00 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         59.67 ± 0.14 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5105.47 ± 38.41 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4756.70 ± 18.63 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.28 ± 0.07 |

build: ff2de1ea9 (11223)
```

#### cwriter_wide_load_and_esimd_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5224.20 ± 20.35 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5024.52 ± 21.29 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.75 ± 0.17 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5082.94 ± 29.81 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4765.83 ± 3.42 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.81 ± 0.99 |

build: c9064dded (11217)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### cwriter_wide_load_and_esimd (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5183.46 ± 18.04 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4970.84 ± 17.08 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.93 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5075.56 ± 27.86 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4730.37 ± 1.86 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         57.19 ± 0.03 |

build: ff2de1ea9 (11223)
```

#### cwriter_wide_load_and_esimd_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5179.15 ± 16.86 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4989.43 ± 3.39 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.99 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5049.54 ± 28.34 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4742.62 ± 0.56 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.30 ± 0.04 |

build: c9064dded (11217)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### cwriter_wide_load_and_esimd (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1340.98 ± 1.29 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1280.94 ± 3.41 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.41 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1310.69 ± 1.08 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1153.30 ± 1.05 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.89 ± 0.01 |

build: ff2de1ea9 (11223)
```

#### cwriter_wide_load_and_esimd_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1341.06 ± 3.76 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1290.10 ± 2.73 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.66 ± 0.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1306.85 ± 2.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1156.96 ± 0.41 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.07 ± 0.19 |

build: c9064dded (11217)
```

- Bench data comparison: different
