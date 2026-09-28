# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29500](https://github.com/ggml-org/llama.cpp/pull/29500) | sycl: add IQ3_S multi-column MMVQ | 2026-09-26T21:50:03Z | @clemenswasser |

## Target Info
- Primary: `clemenswasser_sycl-iq3s-multicol-mmvq`
- Base: `clemenswasser_sycl-iq3s-multicol-mmvq_base`
- Base checked out commit: `81bc6b83f827df746eb129235488d325c49cae52`
- GGUF file: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf`
- GPU: `13th Gen Intel(R) Core(TM) i7-13700K`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| clemenswasser_sycl-iq3s-multicol-mmvq | N/A | N/A | N/A |
| clemenswasser_sycl-iq3s-multicol-mmvq_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | ---: | ---: | ---: | ---: |
| pp512 | 0 | 6015.64 | 6009.65 | -0.10% |
| pp512 | 1 | 6130.19 | 6121.95 | -0.13% |
| tg128 | 0 | 160.29 | 160.88 | 0.37% |
| tg128 | 1 | 162.47 | 162.00 | -0.29% |

## Bench Results

### clemenswasser_sycl-iq3s-multicol-mmvq (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6121.95 ± 16.07 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.00 ± 0.50 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6009.65 ± 21.74 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.88 ± 0.11 |

build: a75e09f41 (11201)
```

### clemenswasser_sycl-iq3s-multicol-mmvq_base (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6130.19 ± 11.91 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.47 ± 0.68 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6015.64 ± 19.25 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        160.29 ± 0.25 |

build: 81bc6b83f (11200)
```

- Bench data comparison from bench.log: different
