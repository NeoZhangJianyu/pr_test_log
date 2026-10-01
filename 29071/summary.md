# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29071](https://github.com/ggml-org/llama.cpp/pull/29071) | [SYCL] fix the issue in mixed different model GPUs in FA | 2026-09-18T08:27:14Z | @arthw |

## Target Info
- Primary: `arthw_fix_mul_gpu_mem`
- Base: `arthw_fix_mul_gpu_mem_base`
- Base checked out commit: `cca7c5f97605aa36b4a88c5bce6b5fcfdd461752`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| arthw_fix_mul_gpu_mem | N/A | N/A | N/A |
| arthw_fix_mul_gpu_mem_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5029.37 | 5040.43 | 0.22% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5152.70 | 5154.64 | 0.04% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4716.64 | 4717.30 | 0.01% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 4962.34 | 4960.83 | -0.03% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 52.03 | 56.69 | 8.96% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 55.49 | 55.88 | 0.70% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5000.85 | 5002.56 | 0.03% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5108.59 | 5115.33 | 0.13% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4685.11 | 4681.83 | -0.07% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4912.08 | 4902.76 | -0.19% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 54.79 | 51.76 | -5.53% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 53.98 | 54.16 | 0.33% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1306.64 | 1325.00 | 1.41% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1352.81 | 1339.56 | -0.98% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1156.44 | 1167.68 | 0.97% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1289.70 | 1290.88 | 0.09% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.45 | 26.96 | -1.79% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.77 | 29.57 | -0.67% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### arthw_fix_mul_gpu_mem (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5154.64 ± 18.19 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4960.83 ± 18.86 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.88 ± 0.06 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5040.43 ± 34.16 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4717.30 ± 4.00 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.69 ± 0.04 |

build: 86f5e5260 (11098)
```

#### arthw_fix_mul_gpu_mem_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5152.70 ± 19.90 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4962.34 ± 18.51 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.49 ± 1.26 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5029.37 ± 28.10 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4716.64 ± 2.01 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         52.03 ± 0.06 |

build: cca7c5f97 (11097)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### arthw_fix_mul_gpu_mem (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5115.33 ± 18.38 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4902.76 ± 17.32 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         54.16 ± 0.56 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5002.56 ± 28.81 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4681.83 ± 4.55 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         51.76 ± 0.06 |

build: 86f5e5260 (11098)
```

#### arthw_fix_mul_gpu_mem_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5108.59 ± 16.75 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4912.08 ± 12.74 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         53.98 ± 0.07 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5000.85 ± 31.80 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4685.11 ± 1.52 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.79 ± 0.02 |

build: cca7c5f97 (11097)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### arthw_fix_mul_gpu_mem (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1339.56 ± 4.56 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1290.88 ± 2.89 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.57 ± 0.14 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1325.00 ± 0.92 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1167.68 ± 1.82 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.96 ± 0.01 |

build: 86f5e5260 (11098)
```

#### arthw_fix_mul_gpu_mem_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1352.81 ± 2.14 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1289.70 ± 2.16 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.77 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1306.64 ± 2.88 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1156.44 ± 1.53 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.45 ± 0.01 |

build: cca7c5f97 (11097)
```

- Bench data comparison: different
