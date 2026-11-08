# llm-serving-lab
환경: Kaggle T4 1장, Qwen2.5-1.5B-Instruct, fp16, HF generate
조건: max_new_tokens=128, do_sample=False
- 요청 1개: 4.71초 (27 토큰/초)
- 순차 4개: 18.96초 (27.0 토큰/초), VRAM 2.89GB
- 배치 4개: 4.85초 (105.6 토큰/초), VRAM 2.92GB → 처리량 약 3.9배

Kaggle T4 1장, Qwen2.5-1.5B-Instruct, fp16, HF generate, max_new_tokens=128
배치 1:  4.74초, 27.0 tok/s, 2.89GB
배치 4:  4.77초, 107.3 tok/s, 2.92GB
배치 8:  4.93초, 207.7 tok/s, 2.96GB
배치 16: 4.92초, 415.9 tok/s, 3.03GB
배치 32: 6.14초, 667.4 tok/s, 3.18GB

import matplotlib.pyplot as plt

bs  = [r[0] for r in results]
tps = [r[2] for r in results]

plt.plot(bs, tps, marker="o")
plt.xlabel("Batch size")
plt.ylabel("Throughput (tokens/s)")
plt.title("HF generate throughput vs batch size (T4, fp16)")
plt.grid(True)
plt.savefig("batch_throughput.png", dpi=150)
plt.show()
