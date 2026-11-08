## Baseline: HF Transformers generate (Kaggle T4, fp16)

Model: Qwen2.5-1.5B-Instruct / max_new_tokens=128 / greedy

| Batch | Time(s) | Throughput(tok/s) | Peak VRAM(GB) |
|---|---|---|---|
| 1  | 4.74 | 27.0  | 2.89 |
| 4  | 4.77 | 107.3 | 2.92 |
| 8  | 4.93 | 207.7 | 2.96 |
| 16 | 4.92 | 415.9 | 3.03 |
| 32 | 6.14 | 667.4 | 3.18 |

![throughput](results/batch_throughput.png)

## vLLM vs HF (Kaggle T4, fp16, Qwen2.5-1.5B-Instruct)

균일 길이(128토큰)
| Batch | HF tok/s | vLLM tok/s |
|---|---|---|
| 1  | 27.0  | 66.8   |
| 4  | 107.3 | 258.0  |
| 8  | 207.7 | 494.8  |
| 16 | 415.9 | 907.9  |
| 32 | 667.4 | 1390.0 |

혼합 길이(32개 요청, 16~256토큰, seed=0, 유효 4850토큰)
| 엔진 | 시간(s) | 유효 tok/s |
|---|---|---|
| HF 정적 배치 | 8.87 | 547.1 |
| vLLM | 5.35 | 905.8 |

HF는 요청별 길이를 지원하지 않아 최대 길이까지 생성하고, 유효 토큰 기준으로 계산함.