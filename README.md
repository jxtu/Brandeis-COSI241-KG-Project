# COSI-241 Final Project
This is the repository for COSI-241 final project.
> Jingxuan Tu, Wei Lu

### Requirements

- python3 (tested on 3.6.6)
- pytorch (tested on 0.4.1)

### Installation

``` bash
python3 -m pip install -r requirements.txt
```

### Data Preparation

Unpack the data files

``` bash
unzip data.zip
```

and there will be a dataset under folder `data`.

``` bash
# dataset mini-NE
data/mini-NE

```

### Pretrain Knowledge Graph Embedding

``` bash
./experiment-emb.sh configs/NE-distmult.sh --train <gpu-ID>
```

`<gpu-ID>` is a non-negative integer number representing the GPU index.

### Meta Learning

``` bash
./experiment-rs.sh configs/NE-rs.sh --train <gpu-ID> --few_shot
```

### Fast Adaptation

``` bash
./experiment-rs.sh configs/NE-rs.sh --train <gpu-ID> --adaptation --checkpoint_path model/mini-NE-point.rs.distmult-xavier-n/a-100-100-2-0.003-0.1-0.1-0.1-256-0.05/checkpoint-<Epoch>.tar
```

`<Epoch>` is a non-negative integer number representing the training epoch for meta-learning.
### Test

``` bash
./experiment-rs.sh configs/NE-rs.sh --inference 1 --few_shot --checkpoint_path model/mini-NE-point.rs.distmult-xavier-n/a-100-100-2-0.003-0.1-0.1-0.1-256-0.05/checkpoint-<Epoch_Adapt>-[relation].tar
```

`<Epoch_Adapt>` is a non-negative integer number representing the training epoch for fast adaptation.


### Resources
1. Original Work
    - MetaKGR: [Adapting Meta Knowledge Graph Information for Multi-Hop Reasoning over Few-Shot Relations](https://arxiv.org/pdf/1908.11513.pdf)
    - MetaKGR codebase: [https://github.com/THU-KEG/MetaKGR](https://github.com/THU-KEG/MetaKGR)
2. Related Material
    - Multi-hop KG baseline: [Multi-Hop Knowledge Graph Reasoning with Reward Shaping](https://arxiv.org/pdf/1808.10568.pdf)
    - Survey on KG: [A Survey on Knowledge Graphs: Representation, Acquisition and Applications](https://arxiv.org/pdf/2002.00388.pdf)
    - One-shot relation learning: [One-Shot Relational Learning for Knowledge Graphs](https://arxiv.org/pdf/1808.09040.pdf)
3. Knowledge Graph Datasets
    - NELL-995: [Original paper](https://arxiv.org/pdf/1707.06690v3.pdf)
    - FB15k-237: [Original paper](https://www.aclweb.org/anthology/W15-4007.pdf)
4. Knowledge Graph Embedding
    - A good introduction: https://aws-dglke.readthedocs.io/en/latest/kg.html#
5. Multi-Hop Reasoning
    - [Policy Gradient](https://medium.com/@jonathan_hui/rl-policy-gradients-explained-9b13b688b146)
6. Meta-Learning
    - A nice tutorial: [Meta-learning is all you need](https://medium.com/cracking-the-data-science-interview/meta-learning-is-all-you-need-3bd0bafdf289)