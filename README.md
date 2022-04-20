# Controlled Text Generation
Reproducing Hu, et. al., ICML 2017's "Toward Controlled Generation of Text" in PyTorch.
This work is for University of Bonn's NLP Lab project on Winter Semester 2017/2018.

## Requirements
Run `pip3 install -r requirements.txt`.

## How to run
1. Run `python3 train_vae.py --save {--gpu}`. This will create `vae.bin`. Essentially this is the base VAE as in Bowman, 2015 [2].
2. Run `python3 train_discriminator --save {--gpu}`. This will create `ctextgen.bin`. The discriminator is using Kim, 2014 [3] architecture and the training procedure is as in Hu, 2017 [1].
3. Run `python3 test.py --model {vae, ctextgen} {--gpu}` for basic evaluations, e.g. conditional generation and latent interpolation.

## Difference compared to the paper
1. Only conditions the model with sentiment, i.e. no tense conditioning.
2. Entirely using SST dataset, which has only ~2800 sentences after filtering. This might not be enough and leads to overfitting. The base VAE in the original model by Hu, 2017 [1] is trained using larger dataset first.
3. Obviously most of the hyperparameters values are different.

## Fixes (2022.04.20 updated)
1. torchtext.data -> torchtext.legacy.data
2. data[0] -> data
3. trivial things ...

## Preview
![result](https://github.com/ybkim95/controlled-text-generation/img/result.png)

## References
1. Hu, Zhiting, et al. "Toward controlled generation of text." International Conference on Machine Learning. 2017. [[pdf](http://proceedings.mlr.press/v70/hu17e/hu17e.pdf)]
2. Bowman, Samuel R., et al. "Generating sentences from a continuous space." arXiv preprint arXiv:1511.06349 (2015). [[pdf](https://arxiv.org/pdf/1511.06349.pdf?utm_campaign=Revue%20newsletter&utm_medium=Newsletter&utm_source=revue)]
3. Kim, Yoon. "Convolutional neural networks for sentence classification." arXiv preprint arXiv:1408.5882 (2014). [[pdf](https://arxiv.org/pdf/1408.5882)]
