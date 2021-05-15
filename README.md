# Flexible Fairness Constraints for Graph Embeddings

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1A2N4yD59Q992NtbiIIuQLTPQeN_r0IjD?usp=sharing)

Paper Link: https://arxiv.org/abs/1905.10674

## Setup

### Dependencies

1. Comet ML for logging. You will need an API key, username, and project name to do online logging.
2. Pytorch version=1.0
3. scikit-learn
4. tqdm for progress bar
5. pickle
6. json
7. joblib
8. networkx for creating reddit graph

### Datasets

- MovieLens-1M (suggested by the paper)

Inside the repository folder :
```bash
# Download Dataset
wget https://download.microsoft.com/download/8/7/0/8700516A-AB3D-4850-B4BB-805C515AECE1/FB15K-237.2.zip
# Unzip Datasets
unzip -qq ./FB15K-237.2.zip
```
- Freebase15k - 237 (new dataset, not tested in the paper)

Inside the repository folder :
```bash
# Download Dataset
wget --no-check-certificate https://files.grouplens.org/datasets/movielens/ml-1m.zip
# Unzip Datasets
unzip -qq ./ml-1m.zip
# Renaming to match path specified in code
mv Release fb15k
```


### Sample Commands
To reproduce the results we provide sample commands. Command Line arguments
control which sensitive attributes are use and whether there is a compositional
adversary or not.

1. FB15k-237:
`ipython --pdb -- paper_trans_e.py --namestr='FB15k Comp Gamma=1000' --do_log
--num_epochs=100 --embed_dim=20 --test_new_disc --sample_mask=True
--use_attr=True --gamma=1000 --valid_freq=50`

2. MovieLens1M:
`ipython --pdb -- main_movielens.py --namestr='100 GCMC Comp and Dummy'
--use_cross_entropy --num_epochs=200 --test_new_disc --use_1M=True
--show_tqdm=True --report_bias=True --valid_freq=5 --use_gcmc=True
--num_classifier_epochs=200 --embed_dim=30 --sample_mask=True --use_attr=True
--gamma=10 --do_log`
