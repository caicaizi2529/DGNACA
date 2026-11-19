# DGNACA

Official PyTorch implementation of DGNACA for session-based recommendation.

Experimental implementation of **Dual-Channel Graph Networks with Attribute-Graph and Context-Aware Aggregation for Session-based Recommendation**.

## Project structure

- `main.py`: training and evaluation entry point and dataset-specific settings.
- `model.py`: model, optimization and ranking metrics.
- `aggregator.py`: attribute and local graph aggregation.
- `utils.py`: data processing and loading.
- `datasets/README.md`: dataset preparation instructions.

## Environment

The implementation requires a CUDA-capable NVIDIA GPU. Install Python, a CUDA-compatible PyTorch build and a matching PyTorch Geometric build, then install the remaining packages listed in `requirements.txt`. Package versions are not pinned.

```bash
python -m pip install -r requirements.txt
```

## Datasets

The datasets are not included in this repository. The [official MGS repository](https://github.com/WHUIR/MGS) provides [preprocessed datasets](https://www.dropbox.com/sh/h548vcds8a4m3qs/AABH-YavkkoNFPR_RMTtmILOa?dl=0) and links to the original data. See [datasets/README.md](datasets/README.md) for the actual MGS download link, expected files and data format.

The `.txt` dataset files are Python pickle files. Load pickle files only from sources you trust.

## Running experiments

Run from the project root:

```bash
python main.py --dataset diginetica
python main.py --dataset Tmall
python main.py --dataset 30music
```

Dataset names are case-sensitive. The seed is 2024. Dataset-specific settings in `main.py` override some command-line arguments. The default procedure evaluates the test set each epoch and uses P@20 and MRR@20 for early stopping; their best values are tracked separately and can occur at different epochs. `--validation` instead splits the preprocessed training examples and evaluates that split. Model-saving statements are commented out.

The program labels hit rate as `Precision@K`; its reported `MRR@K` uses reciprocal rank for hits within the top K.

## Attribution

This implementation includes components derived from the [official MGS implementation](https://github.com/WHUIR/MGS), including `aggregator.py` and `utils.py`.

Lai et al., *An Attribute-Driven Mirror Graph Network for Session-based Recommendation*, SIGIR 2022. https://doi.org/10.1145/3477495.3531935
