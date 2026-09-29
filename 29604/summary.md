# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29604](https://github.com/ggml-org/llama.cpp/pull/29604) | SYCL: reduce tensor allreduce sync with pinned host buffers | 2026-09-28T18:31:00Z | @Captain-Tripps |

## Target Info
- Primary: `Captain-Tripps_sycl-tp-allreduce-pinned`
- Base: `Captain-Tripps_sycl-tp-allreduce-pinned_base`
- Base checked out commit: `6c7a87f7e5e5cd75b8a641c3471f2dee84a6ed17`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| Captain-Tripps_sycl-tp-allreduce-pinned | N/A | N/A | N/A |
| Captain-Tripps_sycl-tp-allreduce-pinned_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5071.83 | 5089.37 | 0.35% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5221.30 | 5225.78 | 0.09% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4777.67 | 4775.05 | -0.05% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5024.21 | 5026.58 | 0.05% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 58.65 | 54.41 | -7.23% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 58.10 | 57.97 | -0.22% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5029.74 | 5048.45 | 0.37% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5177.23 | 5184.04 | 0.13% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4739.93 | 4749.73 | 0.21% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4982.42 | 4987.01 | 0.09% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.11 | 54.27 | 0.30% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.90 | 57.74 | 3.29% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1301.07 | 1319.57 | 1.42% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1348.20 | 1346.50 | -0.13% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1155.38 | 1153.36 | -0.17% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1283.71 | 1286.94 | 0.25% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.23 | 26.88 | -1.29% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.54 | 29.47 | -0.24% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### Captain-Tripps_sycl-tp-allreduce-pinned (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5225.78 ± 15.96 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5026.58 ± 17.14 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.97 ± 0.04 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5089.37 ± 41.05 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4775.05 ± 2.27 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.41 ± 0.77 |

build: 35039c153 (11236)
```

#### Captain-Tripps_sycl-tp-allreduce-pinned_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5221.30 ± 19.48 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5024.21 ± 16.10 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         58.10 ± 0.09 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5071.83 ± 28.99 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4777.67 ± 3.93 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         58.65 ± 0.03 |

build: 6c7a87f7e (11235)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### Captain-Tripps_sycl-tp-allreduce-pinned (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5184.04 ± 19.47 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4987.01 ± 16.00 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.74 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5048.45 ± 31.37 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4749.73 ± 1.00 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.27 ± 0.02 |

build: 35039c153 (11236)
```

#### Captain-Tripps_sycl-tp-allreduce-pinned_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5177.23 ± 19.20 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4982.42 ± 5.22 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.90 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5029.74 ± 33.48 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4739.93 ± 1.39 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.11 ± 0.05 |

build: 6c7a87f7e (11235)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### Captain-Tripps_sycl-tp-allreduce-pinned (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1346.50 ± 5.64 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1286.94 ± 2.86 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.47 ± 0.10 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1319.57 ± 4.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1153.36 ± 1.57 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.88 ± 0.01 |

build: 35039c153 (11236)
```

#### Captain-Tripps_sycl-tp-allreduce-pinned_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1348.20 ± 4.33 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1283.71 ± 3.10 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.54 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1301.07 ± 3.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1155.38 ± 0.52 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.23 ± 0.02 |

build: 6c7a87f7e (11235)
```

- Bench data comparison: different
