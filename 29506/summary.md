# SYCL Workflow Summary

## PR Info

| PR Number | Title | Created | Author |
| ---: | --- | --- | --- |
| [29506](https://github.com/ggml-org/llama.cpp/pull/29506) | sycl: use ExternalProject to let this backend be built with SYCL compiler while everything else could use another | 2026-09-26T23:42:22Z | @a1batross |

## Target Info
- Primary: `a1batross_mix-rocm-sycl-build`
- Base: `a1batross_mix-rocm-sycl-build_base`
- Base checked out commit: `95887577ab5fead779581a7030a83c7752ff3234`
- GGUF file: `Qwen3.5-0.8B-MTP-Q4_K_M.gguf`
- GPU: `13th Gen Intel(R) Core(TM) i7-13700K`

## UT Results

| Target | Passed | UT Cases | Pass Rate |
| --- | ---: | ---: | ---: |
| a1batross_mix-rocm-sycl-build | N/A | N/A | N/A |
| a1batross_mix-rocm-sycl-build_base | N/A | N/A | N/A |

## Bench Throughput Comparison

| Test | fa | Base t/s | Primary t/s | Increase Rate (Primary vs Base) |
| --- | ---: | ---: | ---: | ---: |
| pp512 | 0 | 6010.07 | 6003.43 | -0.11% |
| pp512 | 1 | 6126.97 | 6132.42 | 0.09% |
| tg128 | 0 | 161.57 | 161.11 | -0.28% |
| tg128 | 1 | 163.33 | 162.27 | -0.65% |

## Bench Results

### a1batross_mix-rocm-sycl-build (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6132.42 ± 16.47 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        162.27 ± 0.79 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6003.43 ± 18.44 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        161.11 ± 1.06 |

build: 969134d94 (11207)
```

### a1batross_mix-rocm-sycl-build_base (bench.log)
```text
| model                          |       size |     params | backend    | ngl |  fa | dev          |            test |                  t/s |
| ------------------------------ | ---------: | ---------: | ---------- | --: | --: | ------------ | --------------: | -------------------: |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           pp512 |      6126.97 ± 19.63 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   1 | SYCL0        |           tg128 |        163.33 ± 0.12 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           pp512 |      6010.07 ± 14.81 |
| qwen35 0.8B Q4_K - Medium      | 513.78 MiB |   772.85 M | SYCL       |  -1 |   0 | SYCL0        |           tg128 |        161.57 ± 0.52 |

build: 95887577a (11205)
```

- Bench data comparison from bench.log: different
