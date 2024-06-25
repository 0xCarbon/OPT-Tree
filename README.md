# OPT-Tree: Speculative Decoding with Adaptive Draft Tree Structure

## Contents
- [Introduction](#Introduction)
- [Installation](#installation)
- [Demo](#Inference)
  - [With independent draft models](#With-independent-draft-models)
  - [With EAGLE draft models](#With-EAGLE-draft-models)
- [Evaluation on datasets](#Evaluation-on-datasets)
  - [With independent draft models](#With-independent-draft-models)
  - [With EAGLE draft models](#With-EAGLE-draft-models)

## Introduction
We propose an adaptive and scalable draft tree structure in speculative decoding, which supports for any autoregressive draft models.
![image](https://github.com/Jikai0Wang/OPT-Tree/main/case.png)

## Installation
```bash
pip install -r requirements.txt
```

## Demo
### With independent draft models
```bash
export CUDA_VISIBLE_DEVICES=0 #Also support for multiple GPUs
python demo_opt_classic.py
```
### With EAGLE draft models
```bash
export CUDA_VISIBLE_DEVICES=0 #Also support for multiple GPUs
python demo_opt_eagle.py
```

## Evaluation on datasets
### With independent draft models
```bash
export CUDA_VISIBLE_DEVICES=0,1,2,3
python -m evaluation.eval_opt_classic \
		 --draft-model-path JackFram/llama-68m \
		 --base-model-path meta-llama/Llama-2-7b-chat-hf \
		 --bench-name mt_bench \
		 --answer-file ./mt_classic_opt.jsonl \
		 --temperature 0 \
		 --nodes 60 \
		 --threshold 0.5 \
		 --max_depth 10
```
### With EAGLE draft models
EAGLE draft models can be downloaded from [https://github.com/SafeAILab/EAGLE](https://github.com/SafeAILab/EAGLE)
```bash
export CUDA_VISIBLE_DEVICES=0,1,2,3
python -m evaluation.eval_opt_eagle \
		 --ea-model-path yuhuili/EAGLE-llama2-chat-7B \
		 --base-model-path meta-llama/Llama-2-7b-chat-hf \
		 --bench-name mt_bench \
		 --answer-file ./mt_eagle_opt.jsonl \
		 --temperature 0 \
		 --nodes 60 \
		 --threshold 0.5 \
		 --max_depth 10
```


