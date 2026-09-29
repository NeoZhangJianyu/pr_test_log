# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29247](https://github.com/ggml-org/llama.cpp/pull/29247) | rfc: Memory eliding fusions | 2026-09-21T18:57:06Z | @cwriter |

## Target Info
- Primary: `cwriter_memory_eliding_fusions_with_allocator_fix`
- Base: `cwriter_memory_eliding_fusions_with_allocator_fix_base`
- Base checked out commit: `3d82ef62d47fd74e18f36c5eccbdcf965b617b17`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| cwriter_memory_eliding_fusions_with_allocator_fix | N/A | N/A | N/A |
| cwriter_memory_eliding_fusions_with_allocator_fix_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5017.43 | 5022.66 | 0.10% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5157.93 | 5157.51 | -0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4701.70 | 4700.18 | -0.03% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 4950.85 | 4959.15 | 0.17% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 52.93 | 56.36 | 6.48% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 55.79 | 57.72 | 3.46% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 4987.39 | 4973.21 | -0.28% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5108.55 | 5116.93 | 0.16% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4683.62 | 4671.16 | -0.27% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4909.82 | 4918.11 | 0.17% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.87 | 54.75 | -0.22% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.85 | 55.79 | -0.11% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1307.51 | 1314.11 | 0.50% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1352.36 | 1344.04 | -0.62% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1169.33 | 1157.78 | -0.99% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1291.62 | 1283.13 | -0.66% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.43 | 27.06 | -1.35% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.47 | 29.54 | 0.24% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### cwriter_memory_eliding_fusions_with_allocator_fix (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5157.51 ± 19.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4959.15 ± 3.54 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.72 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5022.66 ± 36.24 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4700.18 ± 0.79 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.36 ± 0.08 |

build: 74196df22 (11066)
```

#### cwriter_memory_eliding_fusions_with_allocator_fix_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5157.93 ± 19.08 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4950.85 ± 20.49 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.79 ± 1.10 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5017.43 ± 37.51 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4701.70 ± 16.79 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         52.93 ± 0.90 |

build: 3d82ef62d (11063)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### cwriter_memory_eliding_fusions_with_allocator_fix (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5116.93 ± 16.06 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4918.11 ± 5.60 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.79 ± 0.48 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4973.21 ± 20.53 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4671.16 ± 3.88 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.75 ± 0.03 |

build: 74196df22 (11066)
```

#### cwriter_memory_eliding_fusions_with_allocator_fix_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5108.55 ± 21.41 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4909.82 ± 18.97 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.85 ± 0.03 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      4987.39 ± 29.41 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4683.62 ± 2.61 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.87 ± 0.01 |

build: 3d82ef62d (11063)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### cwriter_memory_eliding_fusions_with_allocator_fix (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1344.04 ± 3.42 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1283.13 ± 3.57 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.54 ± 0.12 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1314.11 ± 0.93 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1157.78 ± 3.67 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.06 ± 0.21 |

build: 74196df22 (11066)
```

#### cwriter_memory_eliding_fusions_with_allocator_fix_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1352.36 ± 3.95 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1291.62 ± 2.39 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.47 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1307.51 ± 2.69 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1169.33 ± 3.13 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.43 ± 0.03 |

build: 3d82ef62d (11063)
```

- Bench data comparison: different
