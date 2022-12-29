# Prompt-to-Prompt and Structured Diffusion: An efficient implementation

![teaser](docs/teaser.png)
### [Project Page](https://prompt-to-prompt.github.io)&ensp;&ensp;&ensp;[Paper](https://prompt-to-prompt.github.io/ptp_files/Prompt-to-Prompt_preprint.pdf)
### [Project Page](https://weixi-feng.github.io/structure-diffusion-guidance)&ensp;&ensp;&ensp;[Paper](https://arxiv.org/pdf/2212.05032.pdf)

## Original repos

# Prompt-to-Prompt Diffusion
* https://github.com/google/prompt-to-prompt
# Structured Diffusion
* https://github.com/weixi-feng/Structured-Diffusion-Guidance

## How is this repo different from the originals?
* The original version of Prompt-to-Prompt Diffusion requires saving attention weights. This version only requires providing 2 text embeddings for the model, one for the key and one for the value in the attention.
* The original version of Structured Diffusion concatenates each of the aligned noun phrase value embeddings into a Python list, using a custom cross-attention implementation to multiply a common attention map by each encoded value matrix before averaging.
![Original Structured Diffusion Method](https://weixi-feng.github.io/structure-diffusion-guidance/img/method.jpg)
This version directly inputs the (weighted) average of aligned noun phrase value embeddings as the value embedding for the diffusion model. 
  * This allows for a much simpler implementation, and also allows for optimization using memory efficient attention.
  * The only change needed is here: https://github.com/cccntu/diffusers/commit/b43bc04e211f1439ca9bcf47966c17bd43ae310b

## Quickstart

* Take a look at the jupyter notebook for a quick demo: [notebook](prompt_to_prompt.ipynb).
* Everything is in the notebook, except for the 2 lines of code that need to be changed in the diffuser code.

## Setup

* install the version of diffusers, or change it in your own version of diffusers
```
pip install git+https://github.com/cccntu/diffusers@b43bc04e2
```

## Disclaimer

* not all features are implemented.


## Citation

```
@article{hertz2022prompt,
  title={Prompt-to-Prompt Image Editing with Cross Attention Control},
  author={Hertz, Amir and Mokady, Ron and Tenenbaum, Jay and Aberman, Kfir and Pritch, Yael and Cohen-Or, Daniel},
  journal={arXiv preprint arXiv:2208.01626},
  year={2022}
}

@misc{feng2022structured,
  title = {Training-Free Structured Diffusion Guidance for Compositional Text-to-Image Synthesis},
  author = {Feng, Weixi and He, Xuehai and Fu, Tsu-Jui and Jampani, Varun and Akula, Arjun and Narayana, Pradyumna and Basu, Sugato and Wang, Xin Eric and Wang, William Yang},
  journal={arXiv preprint arXiv:2212.05032},
  year={2022}
}
```
