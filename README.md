# Feature-Based vs. Deep Learning Models for 12-Lead ECG Classification

BME 304L final project — Sara Yoon (syy3), Jackie No (jjn22)

We compare a random forest trained on clinical ECG measurements (PTB-XL+, GE 12SL) with a 1D convolutional neural network trained on raw 12-lead signals, on three PTB-XL diagnostic superclasses (NORM, MI, CD).

- **RQ1:** How large is the performance gap (AUROC) between the two models, and for which class is it largest?
- **RQ2:** Which lead groups (inferior, anterior, lateral) does each model rely on, and does this match clinical criteria? This includes a within-class test of inferior vs. anterior MI.

## Data

Both datasets are open access on PhysioNet (CC BY 4.0). The notebook downloads them into `data/` on first run; `data/` is not tracked by git.

- PTB-XL v1.0.3: https://physionet.org/content/ptb-xl/1.0.3/
- PTB-XL+ v1.0.1: https://physionet.org/content/ptb-xl-plus/1.0.1/

## How to run

Requires Python 3.10 or newer. The CNN uses an Apple-chip GPU (PyTorch MPS) if available, otherwise CUDA or CPU.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Open `ecg_analysis.ipynb`, select the `.venv` kernel, and run all cells in order. Before running Section 8 (the first use of the test set), commit `results/expected_lead_groups.json`.

## Repository contents

| Path | Contents |
|---|---|
| `ecg_analysis.ipynb` | Full analysis: data, preprocessing, models, RQ1, RQ2, figures |
| `results/` | Tables (CSV) and `results_summary.json` with every reported number |
| `figures/` | Figures used in the report |
| `data/`, `models/` | Created locally by the notebook; not tracked |
