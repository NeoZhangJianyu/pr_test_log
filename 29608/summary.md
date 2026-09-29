# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29608](https://github.com/ggml-org/llama.cpp/pull/29608) | sycl: stage bulk uploads (model loading) through a pinned ring buffer | 2026-09-28T19:06:58Z | @cwriter |

## Target Info
- Primary: `cwriter_pr-09-sycl-pinned-upload-ring`
- Base: `cwriter_pr-09-sycl-pinned-upload-ring_base`
- Base checked out commit: `a97cce86a8addeb9f40cba7a261c94b1f0c576cb`
- GGUF files: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf, Qwen3.5-0.8B-Q4_K_M.gguf, Qwen2-1.5Moe.Q4_K_M.gguf`
- GPU: `Intel(R) Arc(TM) A770 Graphics`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| cwriter_pr-09-sycl-pinned-upload-ring | N/A | N/A | N/A |
| cwriter_pr-09-sycl-pinned-upload-ring_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| GGUF | Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | --- | ---: | ---: | ---: | ---: |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 0 | 5078.42 | 5081.55 | 0.06% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp512 | 1 | 5226.17 | 5199.19 | -0.52% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 0 | 4768.28 | 4785.56 | 0.36% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | pp8192 | 1 | 5023.20 | 5026.42 | 0.06% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 0 | 54.59 | 53.44 | -2.11% |
| Qwen3.5-0.8B-MTP-Q4_K_M.gguf | tg128 | 1 | 57.30 | 56.88 | -0.73% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 0 | 5054.98 | 5037.87 | -0.34% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp512 | 1 | 5176.24 | 5161.90 | -0.28% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 0 | 4749.50 | 4760.12 | 0.22% |
| Qwen3.5-0.8B-Q4_K_M.gguf | pp8192 | 1 | 4992.64 | 4981.51 | -0.22% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 0 | 56.56 | 55.94 | -1.10% |
| Qwen3.5-0.8B-Q4_K_M.gguf | tg128 | 1 | 55.98 | 56.92 | 1.68% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 0 | 1304.45 | 1309.87 | 0.42% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp512 | 1 | 1350.93 | 1345.58 | -0.40% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 0 | 1155.16 | 1163.12 | 0.69% |
| Qwen2-1.5Moe.Q4_K_M.gguf | pp8192 | 1 | 1290.05 | 1287.42 | -0.20% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 0 | 27.30 | 26.87 | -1.58% |
| Qwen2-1.5Moe.Q4_K_M.gguf | tg128 | 1 | 29.60 | 29.61 | 0.03% |

## Bench Results

### Qwen3.5-0.8B-MTP-Q4_K_M.gguf

#### cwriter_pr-09-sycl-pinned-upload-ring (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5199.19 ± 18.29 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5026.42 ± 11.24 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.88 ± 0.04 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5081.55 ± 28.35 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4785.56 ± 14.71 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         53.44 ± 0.16 |

build: 54a023635 (11223)
```

#### cwriter_pr-09-sycl-pinned-upload-ring_base (bench_1.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5226.17 ± 15.99 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      5023.20 ± 20.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         57.30 ± 1.63 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5078.42 ± 60.25 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |      4768.28 ± 10.65 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         54.59 ± 0.08 |

build: a97cce86a (11222)
```

- Bench data comparison: different

### Qwen3.5-0.8B-Q4_K_M.gguf

#### cwriter_pr-09-sycl-pinned-upload-ring (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5161.90 ± 16.64 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |      4981.51 ± 15.90 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         56.92 ± 0.80 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5037.87 ± 18.36 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4760.12 ± 4.20 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         55.94 ± 0.06 |

build: 54a023635 (11223)
```

#### cwriter_pr-09-sycl-pinned-upload-ring_base (bench_2.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      5176.24 ± 15.28 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       4992.64 ± 2.81 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         55.98 ± 0.05 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      5054.98 ± 32.22 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       4749.50 ± 0.58 |
| qwen35 0.8B Q4_K - Medium      | 497.39 MiB |   752.39 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         56.56 ± 0.06 |

build: a97cce86a (11222)
```

- Bench data comparison: different

### Qwen2-1.5Moe.Q4_K_M.gguf

#### cwriter_pr-09-sycl-pinned-upload-ring (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1345.58 ± 4.57 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1287.42 ± 2.62 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.61 ± 0.02 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1309.87 ± 1.50 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1163.12 ± 1.30 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         26.87 ± 0.08 |

build: 54a023635 (11223)
```

#### cwriter_pr-09-sycl-pinned-upload-ring_base (bench_3.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           pp512 |       1350.93 ± 2.91 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |          pp8192 |       1290.05 ± 2.54 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   1 | SYCL0        |           tg128 |         29.60 ± 0.01 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           pp512 |       1304.45 ± 3.28 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |          pp8192 |       1155.16 ± 0.56 |
| qwen2moe 57B.A14B Q4_K - Medium |   2.34 GiB |     4.09 B | SYCL       |  -1 |   0 | SYCL0        |           tg128 |         27.30 ± 0.01 |

build: a97cce86a (11222)
```

- Bench data comparison: different
