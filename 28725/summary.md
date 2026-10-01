# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [28725](https://github.com/ggml-org/llama.cpp/pull/28725) | Add SYCL graph record and replay | 2026-09-10T23:20:05Z | @malsbat |

## Target Info
- Primary: `aicss-genai_sycl-graph-record-replay`
- Base: `aicss-genai_sycl-graph-record-replay_base`
- Base checked out commit: `58367713a6935c0810103378144008df32e3d5db`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| aicss-genai_sycl-graph-record-replay | N/A | N/A | N/A |
| aicss-genai_sycl-graph-record-replay_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5027.49 | 5047.90 | 0.41% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5149.29 | 5153.24 | 0.08% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4697.95 | 4713.33 | 0.33% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 4946.57 | 4957.90 | 0.23% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 52.85 | 56.59 | 7.08% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 57.90 | 56.00 | -3.28% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 4959.13 | 4993.53 | 0.69% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5114.23 | 5114.85 | 0.01% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4669.16 | 4688.71 | 0.42% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4918.36 | 4912.48 | -0.12% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.75 | 51.82 | -5.35% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.95 | 55.72 | -0.41% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1308.84 | 1307.21 | -0.12% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1339.15 | 1338.73 | -0.03% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1154.37 | 1155.37 | 0.09% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1282.39 | 1287.33 | 0.39% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.01 | 27.40 | 1.44% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.52 | 29.59 | 0.24% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### aicss-genai_sycl-graph-record-replay (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5153.24 ± 15.64 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4957.90 ± 16.73 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.00 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5047.90 ± 33.23 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4713.33 ± 2.93 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.59 ± 0.15 |

build: 477a1f1f3 (11101)
```

#### aicss-genai_sycl-graph-record-replay_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5149.29 ± 19.84 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4946.57 ± 21.69 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.90 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5027.49 ± 32.20 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4697.95 ± 2.38 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         52.85 ± 0.92 |

build: 58367713a (11095)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### aicss-genai_sycl-graph-record-replay (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5114.85 ± 20.43 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4912.48 ± 16.00 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.72 ± 0.64 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4993.53 ± 25.43 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4688.71 ± 2.50 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         51.82 ± 0.88 |

build: 477a1f1f3 (11101)
```

#### aicss-genai_sycl-graph-record-replay_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5114.23 ± 16.40 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4918.36 ± 7.21 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.95 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4959.13 ± 62.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4669.16 ± 6.10 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.75 ± 0.01 |

build: 58367713a (11095)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### aicss-genai_sycl-graph-record-replay (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1338.73 ± 3.63 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1287.33 ± 1.96 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.59 ± 0.14 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1307.21 ± 1.75 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1155.37 ± 1.42 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.40 ± 0.01 |

build: 477a1f1f3 (11101)
```

#### aicss-genai_sycl-graph-record-replay_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1339.15 ± 2.52 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1282.39 ± 2.15 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.52 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1308.84 ± 3.33 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1154.37 ± 1.53 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.01 ± 0.01 |

build: 58367713a (11095)
```

- Bench data comparison: different
