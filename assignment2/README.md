# Implementation notes

- Q1.1. is self-contained in the notebook [part0_q11/DL1_Assignment2_Q1_1.ipynb](part0/DL1_Assignment2_Q1_1.ipynb)
- All other experiments are implemented as Snellius jobs, so they are reproducible. 
  - Resnet: [part1/run_resnet18.job](part1/run_resnet18.job)
  - Zero-shot: [part2/run_clip_zs.job](part2/run_clip_zs.job)
  - Visual prompting: [part2/run_clip_vp.job](part2/run_clip_vp.job)
  - Deep prompting: [part2/run_clip_dp.job](part2/run_clip_dp.job)
- Each execution saves its parameters and results as a small json file in order to make result collection easy. The results from my executions are in [snellius_results](snellius_results)
- All results are collected, combined and visualized in the notebook [evaluate.ipynb](evaluate.ipynb)
  - All plots are created with Plotly, so please install the `plotly` and `kaleido` packages if you want to reproduce them

Thanks for checking this out!

# Assignment 2: Transfer Learning for CNNs, Visual Prompting (and GNNs)

The assignment is organized in two parts (as GNNs don't have any implementation questions). The first part covers transfer learning for CNNs, where you fine-tune an existing network to adapt it to a new dataset. In the second part, you prompt CLIP to perform image classification, both in the zero-shot setting and by learning a visual prompt.

When submitting your code, __make sure to not include the trained models and/or the CIFAR datasets__.

## Part 1: Transfer Learning for CNNs
* [No template code] Compare popular CNN architectures on ImageNet using data from the [PyTorch website](https://pytorch.org/vision/stable/models.html#table-of-all-available-classification-weights).
* [No template code] Use the official PyTorch implementations to compute and compare the inference speed, memory usage, and parameter count for the same models.
* Adapt a ResNet-18 model from ImageNet to CIFAR-100 by resetting its last layer.
* Perform augmentations to improve performance.

## Part 2: Visual Prompting
* Install CLIP using the `install_clip.job` job file (Hint: `pip install clip` won't work).
* Evaluate CLIP-B/32 in the zero-shot setting on CIFAR-10 and CIFAR-100 (`clipzs.py`).
* Prompt CLIP on two new downstream tasks by changing the text template (`--prompt`) and class labels (`--class_names`). You can visualize your predictions with `--visualize_predictions`.
* Learn visual prompts for the CIFAR-10 and CIFAR-100 datasets (`learner.py`, `vpt_model.py`, `vp.py`).
* Experiment with the prompt design to get near-random performance on CIFAR-100.
* Evaluate the robustness of the learnt prompts to distributional shifts (`robustness.py`).
* Evaluate each dataset's learnt prompt on the concatenation of both CIFAR-10 and CIFAR-100 (`cross_dataset.py`).
