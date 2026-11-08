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