# LLM Quantization Benchmark

AIMultiple comparison of Qwen3-32B at BF16, FP8, GPTQ-Int8 and GPTQ-Int4 precision on a single H100 80 GB GPU. The study measures generation speed, memory use and accuracy with vLLM.

> [Read the benchmark on AIMultiple](https://aimultiple.com/llm-quantization)

## Benchmark results

Throughput uses batch size 1 and 256-token generations. MMLU-Pro measures knowledge and reasoning accuracy. HumanEval pass@1 measures whether generated code passes its tests on the first attempt.

| Precision | Output tokens/s | MMLU-Pro | HumanEval pass@1 |
| --- | ---: | ---: | ---: |
| BF16 | 26.0 | 70.24% | 39.02% |
| FP8 | 37.9 | 69.64% | 39.02% |
| GPTQ-Int8 | 43.3 | 70.32% | 37.20% |
| GPTQ-Int4 | 69.9 | 68.66% | 31.10% |

INT4 increases throughput by about 2.7 times relative to BF16. Its accuracy loss is larger on code generation than on MMLU-Pro. FP8 preserves the measured HumanEval score while reducing model memory.

The comparison covers one model and GPU. Concurrency figures in the article are capacity estimates derived from memory use. Live load testing is outside that calculation.

## Ownership

The benchmark implementation was developed for AIMultiple and belongs to AIMultiple. This repository contains a documentation summary. Source code and benchmark datasets are not distributed here.
