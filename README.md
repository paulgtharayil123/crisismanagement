# Multimodal Identification of Informative Social Media Posts for Disaster Response

Does combining a tweet's **text** with its **image** help find *informative* disaster posts
better than using text or image alone? This repo compares six models on **CrisisMMD v2.0**.

## Repository structure

```
CrisisMMD_project.ipynb   - MAIN FILE: the whole project in one notebook (with outputs)
requirements.txt
results/                  - tables (.csv/.json) and figures produced by the notebook
```

## How to reproduce

**Step 1 — install the libraries** 
**Step 2 — open the notebook "CrisisMMD_project.ipynb" and run all cells, top to bottom**


Everything is downloaded from inside the notebook so no separate commands needed:


Settings are in the first code cell: `MAX_PER_SPLIT = 500, SEEDS = [0]` gives a quick test (and downloads only
those images); `MAX_PER_SPLIT = None, SEEDS = [0, 1, 2]` gives the full results reported


## Data

[QCRI/CrisisMMD](https://huggingface.co/datasets/QCRI/CrisisMMD), config `informative`
(CC BY-NC-SA 4.0). 18,082 tweet–image pairs from 7 disasters in 2017, using the official
splits: train 13,608 / dev 2,237 / test 2,237. Label: `informative` (1) vs `not_informative` (0).
The dataset downloads automatically on first run.

## Outputs (`results/`)

* `data_quality.json` - the data quality check 
* `summary_table.csv` - test metrics per model, mean ± std 
* `metrics_by_seed.csv` - every metric for every model and seed 
* `overfitting_efficiency.csv` - train vs dev vs test F1, parameters, training time, inference time 
* `per_event_f1.csv`, `leave_one_event_out.csv`, `loeo_vs_indist.csv` - per-disaster and unseen-disaster results 
* `agreement_text_vs_*.csv` - test posts fixed / broken by adding the image 
* `seen_vs_new_text.csv` - score on test tweets whose text also appears in train vs new text 
* `uncertainty_coverage.csv` - macro-F1 when the most uncertain posts go to a human 
* `figures/fig0…fig11` - all figures used in the report and slides 
