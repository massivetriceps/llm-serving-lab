# llm-serving-lab
환경: Kaggle T4 1장, Qwen2.5-1.5B-Instruct, fp16, HF generate
조건: max_new_tokens=128, do_sample=False
- 요청 1개: 4.71초 (27 토큰/초)
- 순차 4개: 18.96초 (27.0 토큰/초), VRAM 2.89GB
- 배치 4개: 4.85초 (105.6 토큰/초), VRAM 2.92GB → 처리량 약 3.9배
