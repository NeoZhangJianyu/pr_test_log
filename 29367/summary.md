# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29367](https://github.com/ggml-org/llama.cpp/pull/29367) | [SYCL] convert function-pointer NTTP templates in cpy.cpp to integer | 2026-09-24T09:54:39Z | @mctylr-gh |

## Target Info
- Primary: `mctylr-gh_sycl-nttp-workaround`
- Base: `mctylr-gh_sycl-nttp-workaround_base`
- Base checked out commit: `4b1a27fa0eb875bbca4f6cfe936e3d65adc685c0`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| mctylr-gh_sycl-nttp-workaround | N/A | N/A | N/A |
| mctylr-gh_sycl-nttp-workaround_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5103.95 | 5104.62 | 0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5221.74 | 5225.99 | 0.08% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4762.30 | 4748.74 | -0.28% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5011.61 | 5023.71 | 0.24% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.55 | 54.55 | -6.83% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 58.01 | 57.95 | -0.10% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5037.75 | 5073.38 | 0.71% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5181.57 | 5183.22 | 0.03% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4723.44 | 4728.82 | 0.11% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4986.15 | 4972.48 | -0.27% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 56.50 | 54.18 | -4.11% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 57.62 | 56.00 | -2.81% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1307.54 | 1306.04 | -0.11% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1338.62 | 1338.53 | -0.01% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1151.11 | 1153.95 | 0.25% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1283.48 | 1281.66 | -0.14% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.31 | 27.17 | -0.51% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.46 | 29.55 | 0.31% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### mctylr-gh_sycl-nttp-workaround (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5225.99 ± 15.66 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5023.71 ± 16.43 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.95 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5104.62 ± 40.33 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4748.74 ± 18.35 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.55 ± 0.05 |

build: 5cce2556b (11195)
```

#### mctylr-gh_sycl-nttp-workaround_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5221.74 ± 18.33 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5011.61 ± 17.66 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.01 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5103.95 ± 36.95 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4762.30 ± 1.44 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.55 ± 0.05 |

build: 4b1a27fa0 (11191)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### mctylr-gh_sycl-nttp-workaround (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5183.22 ± 22.96 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4972.48 ± 21.10 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.00 ± 0.09 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5073.38 ± 32.67 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4728.82 ± 1.44 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.18 ± 0.02 |

build: 5cce2556b (11195)
```

#### mctylr-gh_sycl-nttp-workaround_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5181.57 ± 14.74 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4986.15 ± 4.74 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.62 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5037.75 ± 37.44 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4723.44 ± 4.69 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.50 ± 0.23 |

build: 4b1a27fa0 (11191)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### mctylr-gh_sycl-nttp-workaround (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1338.53 ± 3.03 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1281.66 ± 2.76 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.55 ± 0.10 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1306.04 ± 2.10 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1153.95 ± 4.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.17 ± 0.24 |

build: 5cce2556b (11195)
```

#### mctylr-gh_sycl-nttp-workaround_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1338.62 ± 2.13 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1283.48 ± 4.48 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.46 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1307.54 ± 2.68 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1151.11 ± 1.79 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.31 ± 0.06 |

build: 4b1a27fa0 (11191)
```

- Bench data comparison: different
