# Run GPT With Colossal-AI

## Overview

**We recommend you read the [readme](../gpt_2/readme.md) file in gpt-2 first.**

GPT-3 is a really huge model, for which it seems not possible to train it with a little number of GPUs. Therefore, we choose some common sets of parameters instead of the smallest ones.

Here are our default parameters of GPT-3 configs:

| config         | GPU* | batch size | TP   | PP   | DP   |
| -------------- | ---- | ---------- | ---- | ---- | ---- |
| gpt3_pp1d_min  | 96   | 192        | 4    | 24   | 1    |
| gpt3_pp1d      | 128  | 192        | 4    | 32   | 1    |
| gpt3_pp2d      | 96   | 2*48       | 4    | 24   | 1    |
| gpt3_pp2p5d    | 96   | 2*48       | 4    | 24   | 1    |
| gpt3_zero3_min | 64   | 3          | 1    | 1    | 64   |
| gpt3_zero3     | 96   | 2          | 1    | 1    | 96   |

*\*Note: For GPUs, we use Nvidia A100 40G.*

In the figure above, `_min` means the set of parameters requires the least number of GPUs with the same mode.

GPT-3 and GPT-2 have the same set of parameter.

**We recommend you read the `readme`file in gpt-2 first.**

## **USAGE**

```Bash
#!/usr/bin/env sh
export DATA=/path/to/train_data.json

torchrun --standalone --nproc_per_node=no_gpus train_gpt.py --config=gpt3_configs/files --from_torch
```

You can copy it and save it as `run.sh` and use `./run.sh` to run the script in your terminal.

Please modify `DATA`, `no_gpus` and `gpt3_configs/files` with the path to your dataset, the number of GPUs and the config file path, respectively.