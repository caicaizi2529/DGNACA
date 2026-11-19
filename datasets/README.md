# Datasets

Data files are not included. The [official MGS repository](https://github.com/WHUIR/MGS) describes Diginetica, Tmall and 30Music and provides a [preprocessed data download](https://www.dropbox.com/sh/h548vcds8a4m3qs/AABH-YavkkoNFPR_RMTtmILOa?dl=0) and links to original datasets. Place compatible preprocessed files under `datasets/diginetica/`, `datasets/Tmall/` and `datasets/30music/`.

Each directory must contain:

- `train.txt` and `test.txt`: Python pickle files containing `(input_sequences, target_items)`.
- `product_attributes.json`: item-ID-keyed attribute information and neighbor item lists. Diginetica and 30Music use `same_cate`; Tmall uses `same_cate` and `same_brand`. Neighbor IDs must use the same item-ID mapping as the sequences.

Zero is reserved for padding. Run the training entry point from the repository root. Downloaded data and mappings should be checked against the requirements above before use. Only load pickle files from trusted sources.
