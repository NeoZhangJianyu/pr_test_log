# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29507](https://github.com/ggml-org/llama.cpp/pull/29507) | sycl: remove duplicate block-size defines from op headers | 2026-09-27T02:11:37Z | @Titaniumtown |

## Target Info
- Primary: `Titaniumtown_pr-blockdup`
- Base: `Titaniumtown_pr-blockdup_base`
- Base checked out commit: `08618ff8e735141d8e4e5be28e6d6af170e4757b`
- GGUF file: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: |
| Titaniumtown_pr-blockdup | N/A | N/A | N/A |
| Titaniumtown_pr-blockdup_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | ---: | ---: | ---: | ---: |
| pp512 | 0 | 6017.30 | 6011.35 | -0.10% |
| pp512 | 1 | 6133.18 | 6131.28 | -0.03% |
| tg128 | 0 | 160.88 | 160.68 | -0.12% |
| tg128 | 1 | 161.94 | 161.98 | 0.02% |

## Bench Results

### Titaniumtown_pr-blockdup (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6131.28 ± 18.60 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        161.98 ± 0.15 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6011.35 ± 17.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.68 ± 0.18 |

build: a2b724c44 (11199)
```

### Titaniumtown_pr-blockdup_base (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6133.18 ± 18.21 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        161.94 ± 0.16 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6017.30 ± 15.65 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.88 ± 0.15 |

build: 08618ff8e (11198)
```

- Bench data comparison from bench.log: different
