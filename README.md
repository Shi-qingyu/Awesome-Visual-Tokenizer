[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![PR's Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](https://github.com/lxtGH/Awesome-Visual-Tokenizer/pulls)
<br />
<p align="center">
  <h1 align="center">Visual Tokenizers: A Comprehensive Survey</h1>
  <p align="center">
     Technical Report [Survey], 2026
    <br />
    <a href="https://msalab-pku.github.io/authors/qyshi/"><strong>Qingyu Shi</strong></a>
    ·
    <a href="https://yuanhaobo.me/"><strong>Haobo Yuan</strong></a>
    ·
    <a href="https://scholar.google.com/citations?user=dZikW2YAAAAJ"><strong>Yikang Zhou</strong></a>
    ·
    <a href="https://www.sigs.tsinghua.edu.cn/lx_en/main.htm"><strong>Xiu Li</strong></a>
    ·
    <a href="https://lxtgh.github.io/"><strong>Jason Li</strong></a>
    ·
    <a href="https://wusize.github.io/"><strong>Size Wu</strong></a>
    ·
    <a href="https://haochen-wang409.github.io/"><strong>Haochen Wang</strong></a>
    <br />
    <a href="https://tyfeld.github.io/"><strong>Ye Tian</strong></a>
    ·
    <a href="https://zhang-tao-whu.github.io/"><strong>Tao Zhang</strong></a>
    ·
    <a href="https://noyii.github.io/"><strong>Jinbin Bai</strong></a>
    ·
    <a href="https://scholar.google.com/citations?user=YgL4rywAAAAJ&hl=en"><strong>Yujing Wang</strong></a>
    ·
    <a href="http://luqi.info/"><strong>Lu Qi</strong></a>
    ·
    <a href="https://msalab-pku.github.io/authors/yhtong/"><strong>Yunhai Tong</strong></a>
    ·
    <a href="https://faculty.ucmerced.edu/mhyang/"><strong>Ming-Hsuan Yang</strong></a>
  </p>

  <p align="center">
    <a href='./paper/tokenizer_survey_project.pdf'>
      <img src='https://img.shields.io/badge/Paper-PDF-green?style=flat&logo=adobeacrobatreader&logoColor=red' alt='Paper PDF'>
    </a>
  </p>
<br />

This repo records, tracks, and organizes papers on **visual tokenizers** as a supplement to our [survey](./paper/tokenizer_survey_project.pdf), following its taxonomy.

## Summary

Visual tokenization transforms high-dimensional visual data into compact sequences, bridging images, videos, and 3D content with sequence modeling. The survey distinguishes task-specific tokenizers from unified tokenizers according to the information their representations preserve and the downstream tasks they support.

- **Task-Specific Tokenizers (§3):** high-level semantic tokenizers for recognition, retrieval, and dense prediction; low-level tokenizers for reconstruction and generation, organized by reconstruction fidelity, compression efficiency, and disentanglement.
- **Unified Tokenizers (§4):** representations that combine semantics and visual details, organized into single-encoder methods that enhance or preserve semantics, and dual-encoder methods with parallel or cascade architectures.
- **Unified Multimodal Systems (§5.3):** model-level understanding and generation can also use one task-specific tokenizer or separate task-specific tokenizers. These systems are listed separately, following Table 9.

## Contents

- [Task-Specific Tokenizers](#task-specific-tokenizers)
- [Unified Tokenizers](#unified-tokenizers)
- [Unified Multimodal Systems Using Task-Specific Tokenizers](#unified-multimodal-systems-using-task-specific-tokenizers)
- [Task and Modality Extensions](#task-and-modality-extensions)
- [Related Generation and Background References](#related-generation-and-background-references)
- [Citation](#citation)

Notes:

- Section numbers and table numbers refer to the [survey PDF](./paper/tokenizer_survey_project.pdf). Architectural assignments follow §4 and Tables 1–4; benchmark tables provide additional comparisons of methods and systems.
- Dataset, curation, inference, and generation references are identified separately from tokenizer methods. Supplementary methods are labeled when the survey does not give a detailed architectural assignment.
- `-` in **Code / Project** means no link is recorded here; it does not imply that no public implementation exists.

## Task-Specific Tokenizers

### High-Level Tokenizers

[Survey §3.1](./paper/tokenizer_survey_project.pdf#page=7). These encoders emphasize semantic abstraction for classification, retrieval, and spatial understanding. The survey groups them by training strategy and also reviews data scaling.

#### Supervised Learning: Strong Supervision

Learning visual representations from curated human annotations (§3.1.1).

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| AlexNet | ImageNet Classification with Deep Convolutional Neural Networks | [Paper](https://papers.nips.cc/paper_files/paper/2012/hash/c399862d3b9d6b76c8436e924a68c45b-Abstract.html) | - |
| VGG | Very Deep Convolutional Networks for Large-Scale Image Recognition | [Paper](https://arxiv.org/abs/1409.1556) | - |
| ResNet | Deep Residual Learning for Image Recognition | [Paper](https://arxiv.org/abs/1512.03385) | - |
| ViT | An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale | [Paper](https://arxiv.org/abs/2010.11929) | - |
| Swin Transformer | Swin Transformer: Hierarchical Vision Transformer using Shifted Windows | [Paper](https://arxiv.org/abs/2103.14030) | - |
| ConvNeXt | A ConvNet for the 2020s | [Paper](https://arxiv.org/abs/2201.03545) | - |

#### Supervised Learning: Weak Supervision

Learning transferable semantics from web-scale image-text pairs (§3.1.1).

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| CLIP | Learning Transferable Visual Models From Natural Language Supervision | [Paper](https://arxiv.org/abs/2103.00020) | - |
| ALIGN | Scaling Up Visual and Vision-Language Representation Learning With Noisy Text Supervision | [Paper](https://arxiv.org/abs/2102.05918) | - |
| LiT | LiT: Zero-Shot Transfer with Locked-image text Tuning | [Paper](https://arxiv.org/abs/2111.07991) | - |
| SigLIP | Sigmoid Loss for Language Image Pre-Training | [Paper](https://arxiv.org/abs/2303.15343) | - |
| SigLIP 2 | SigLIP 2: Multilingual Vision-Language Encoders with Improved Semantic Understanding, Localization, and Dense Features | [Paper](https://arxiv.org/abs/2502.14786) | - |
| Perception Encoder | Perception Encoder: The best visual embeddings are not at the output of the network | [Paper](https://arxiv.org/abs/2504.13181) | - |

#### Self-Supervised Learning: Predictive Methods

Predicting missing pixels, tokens, or latent features (§3.1.1). DAE and iBOT are also shown in the taxonomy figure (Fig. 1); EVA and TIPS combine predictive learning with vision-language supervision.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| DAE | Extracting and Composing Robust Features with Denoising Autoencoders | [Paper](https://icml.cc/2008/papers/592.pdf) | - |
| BEiT | BEiT: BERT Pre-Training of Image Transformers | [Paper](https://arxiv.org/abs/2106.08254) | - |
| iBOT | iBOT: Image BERT Pre-Training with Online Tokenizer | [Paper](https://arxiv.org/abs/2111.07832) | - |
| MAE | Masked Autoencoders Are Scalable Vision Learners | [Paper](https://arxiv.org/abs/2111.06377) | - |
| I-JEPA | Self-Supervised Learning from Images with a Joint-Embedding Predictive Architecture | [Paper](https://arxiv.org/abs/2301.08243) | - |
| EVA | EVA: Exploring the Limits of Masked Visual Representation Learning at Scale | [Paper](https://arxiv.org/abs/2211.07636) | - |
| TIPS | TIPS: Text-Image Pretraining with Spatial awareness | [Paper](https://arxiv.org/abs/2410.16512) | - |

#### Self-Supervised Learning: Discriminative Methods

Learning invariant representations through contrastive learning or self-distillation (§3.1.1).

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| MoCo | Momentum Contrast for Unsupervised Visual Representation Learning | [Paper](https://arxiv.org/abs/1911.05722) | - |
| MoCo v3 | An Empirical Study of Training Self-Supervised Vision Transformers | [Paper](https://arxiv.org/abs/2104.02057) | - |
| SimCLR | A Simple Framework for Contrastive Learning of Visual Representations | [Paper](https://arxiv.org/abs/2002.05709) | - |
| BYOL | Bootstrap your own latent: A new approach to self-supervised Learning | [Paper](https://arxiv.org/abs/2006.07733) | - |
| DINO | Emerging Properties in Self-Supervised Vision Transformers | [Paper](https://arxiv.org/abs/2104.14294) | - |
| DINOv2 | DINOv2: Learning Robust Visual Features without Supervision | [Paper](https://arxiv.org/abs/2304.07193) | - |
| DINOv3 | DINOv3 | [Paper](https://arxiv.org/abs/2508.10104) | - |

#### Distillation: Efficient Models

Transferring teacher representations to smaller encoders (§3.1.1). DINOv3, listed above, also uses multi-student distillation.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| DeiT | Training data-efficient image transformers & distillation through attention | [Paper](https://arxiv.org/abs/2012.12877) | - |
| TinyMIM | TinyMIM: An Empirical Study of Distilling MIM Pre-trained Models | [Paper](https://arxiv.org/abs/2301.01296) | - |
| DMAE | Masked Autoencoders Enable Efficient Knowledge Distillers | [Paper](https://arxiv.org/abs/2208.12256) | - |
| EdgeSAM | EdgeSAM: Prompt-In-the-Loop Distillation for SAM | [Paper](https://arxiv.org/abs/2312.06660) | - |

#### Distillation: Agglomerative Strategies

Combining complementary semantic, spatial, and dense capabilities from multiple vision foundation models (§3.1.1).

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| AM-RADIO | AM-RADIO: Agglomerative Vision Foundation Model -- Reduce All Domains Into One | [Paper](https://arxiv.org/abs/2312.06709) | - |
| RADIOv2.5 | RADIOv2.5: Improved Baselines for Agglomerative Vision Foundation Models | [Paper](https://arxiv.org/abs/2412.07679) | - |
| C-RADIOv3-L | C-RADIOv3-L (Hugging Face model card) | [Model Card](https://huggingface.co/nvidia/C-RADIOv3-L) | - |
| C-RADIOv4 | C-RADIOv4 (Tech Report) | [Paper](https://arxiv.org/abs/2601.17237) | - |
| SAM-CLIP | SAM-CLIP: Merging Vision Foundation Models towards Semantic and Spatial Understanding | [Paper](https://arxiv.org/abs/2310.15308) | - |
| Open-Vocabulary SAM | Open-Vocabulary SAM: Segment and Recognize Twenty-thousand Classes Interactively | [Paper](https://arxiv.org/abs/2401.02955) | - |
| Theia | Theia: Distilling Diverse Vision Foundation Models for Robot Learning | [Paper](https://arxiv.org/abs/2407.20179) | - |

#### Data Scaling: Real and Synthetic Data

Supporting datasets and data-generation studies from §3.1.2. These entries describe the training data and supervision used to improve semantic encoders.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| ImageNet | ImageNet Large Scale Visual Recognition Challenge | [Paper](https://arxiv.org/abs/1409.0575) | - |
| JFT-300M | Revisiting Unreasonable Effectiveness of Data in Deep Learning Era | [Paper](https://arxiv.org/abs/1707.02968) | - |
| LAION-5B | LAION-5B: An open large-scale dataset for training next generation image-text models | [Paper](https://arxiv.org/abs/2210.08402) | - |
| DataComp | DataComp: In search of the next generation of multimodal datasets | [Paper](https://arxiv.org/abs/2304.14108) | - |
| WebLI-100B | Scaling Pre-training to One Hundred Billion Data for Vision Language Models | [Paper](https://arxiv.org/abs/2502.07617) | - |
| StableRep | StableRep: Synthetic Images from Text-to-Image Models Make Strong Visual Representation Learners | [Paper](https://arxiv.org/abs/2306.00984) | - |
| CapsFusion | CapsFusion: Rethinking Image-Text Data at Scale | [Paper](https://arxiv.org/abs/2310.20550) | - |
| SynCLR | Learning Vision from Models Rivals Learning Vision from Data | [Paper](https://arxiv.org/abs/2312.17742) | - |

#### Data Scaling: Curation and Sampling

Clustering, balancing, and sampling studies from §3.1.2. DINOv3 also uses mixed homogeneous and heterogeneous batch sampling.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| MetaCLIP | Demystifying CLIP Data | [Paper](https://arxiv.org/abs/2309.16671) | - |
| Automatic Data Curation | Automatic Data Curation for Self-Supervised Learning: A Clustering-Based Approach | [Paper](https://arxiv.org/abs/2405.15613) | - |
| Two-set Training | Emergent properties with repeated examples | [Paper](https://arxiv.org/abs/2410.07041) | - |

#### Additional Perception Encoders

A related image/video understanding encoder included in the survey references. OneVision-Encoder uses codec-aligned sparsity to improve semantic encoding.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| OneVision-Encoder | OneVision-Encoder: Codec-Aligned Sparsity as a Foundational Principle for Multimodal Intelligence | [Paper](https://arxiv.org/abs/2602.08683) | [EvolvingLMMs-Lab/OneVision-Encoder](https://github.com/EvolvingLMMs-Lab/OneVision-Encoder) |

### Low-Level Tokenizers

[Survey §3.2](./paper/tokenizer_survey_project.pdf#page=9). These methods preserve visual details in compact latent representations. The four groups below follow §§3.2.1–3.2.4. Compression is an objective that applies to both continuous and discrete tokenizers; methods are listed under the main role discussed in the survey.

#### Continuous Tokenizers: Reconstruction Fidelity

§3.2.1 discusses posterior collapse, expressive priors, hierarchical latent spaces, and reconstruction objectives. DiTo belongs to this continuous reconstruction group; the tokenizer used by LDM is identified as SD-VAE.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| VAE | Auto-Encoding Variational Bayes | [Paper](https://arxiv.org/abs/1312.6114) | - |
| AAE | Adversarial Autoencoders | [Paper](https://arxiv.org/abs/1511.05644) | - |
| LVAE | Ladder Variational Autoencoders | [Paper](https://arxiv.org/abs/1602.02282) | - |
| GMVAE | Deep Unsupervised Clustering with Gaussian Mixture Variational Autoencoders | [Paper](https://arxiv.org/abs/1611.02648) | - |
| VampPrior | VAE with a VampPrior | [Paper](https://arxiv.org/abs/1705.07120) | - |
| ARAE | Adversarially Regularized Autoencoders | [Paper](https://arxiv.org/abs/1706.04223) | - |
| WAE | Wasserstein Auto-Encoders | [Paper](https://arxiv.org/abs/1711.01558) | - |
| Sliced-WAE | Sliced Wasserstein Auto-Encoders | [Paper](https://arxiv.org/abs/1804.01947) | - |
| IntroVAE | IntroVAE: Introspective Variational Autoencoders for Photographic Image Synthesis | [Paper](https://arxiv.org/abs/1807.06358) | [hhb072/IntroVAE](https://github.com/hhb072/IntroVAE) |
| VAIOP | Variational Autoencoder with Implicit Optimal Priors | [Paper](https://arxiv.org/abs/1809.05284) | - |
| BIVA | BIVA: A Very Deep Hierarchy of Latent Variables for Generative Modeling | [Paper](https://arxiv.org/abs/1902.02102) | - |
| NVAE | NVAE: A Deep Hierarchical Variational Autoencoder | [Paper](https://arxiv.org/abs/2007.03898) | [NVlabs/NVAE](https://github.com/NVlabs/NVAE) |
| - | A Contrastive Learning Approach for Training Variational Autoencoder Priors | [Paper](https://arxiv.org/abs/2010.02917) | - |
| VDVAE | Very Deep VAEs Generalize Autoregressive Models and Can Outperform Them on Images | [Paper](https://arxiv.org/abs/2011.10650) | - |
| Soft-IntroVAE | Soft-IntroVAE: Analyzing and Improving the Introspective Variational Autoencoder | [Paper](https://arxiv.org/abs/2012.13253) | [taldatech/soft-intro-vae-pytorch](https://github.com/taldatech/soft-intro-vae-pytorch) |
| SD-VAE (LDM) | High-Resolution Image Synthesis with Latent Diffusion Models | [Paper](https://arxiv.org/abs/2112.10752) | [CompVis/latent-diffusion](https://github.com/CompVis/latent-diffusion) |
| DiTo | Diffusion Autoencoders are Scalable Image Tokenizers | [Paper](https://arxiv.org/abs/2501.18593) | [yinboc/dito](https://github.com/yinboc/dito) |

Additional continuous autoencoder designs and tokenizer training/tuning studies. REPA-E jointly tunes the VAE and diffusion model, yielding E2E-VAE; l-DeTok is also evaluated as a continuous tokenizer in Table 6.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| - | Variational Autoencoder for Deep Learning of Images, Labels, and Captions | [Paper](https://arxiv.org/abs/1609.08976) | - |
| CR-VAE | Consistency Regularization for Variational Auto-Encoders | [Paper](https://arxiv.org/abs/2105.14859) | - |
| ViTok | Learnings from Scaling Visual Tokenizers for Reconstruction and Generation | [Paper](https://arxiv.org/abs/2501.09755) | [Project Page](https://vitok.github.io/) |
| EQ-VAE | EQ-VAE: Equivariance Regularized Latent Space for Improved Generative Image Modeling | [Paper](https://arxiv.org/abs/2502.09509) | [zelaki/eqvae](https://github.com/zelaki/eqvae) |
| Diffusability | Improving the Diffusability of Autoencoders | [Paper](https://arxiv.org/abs/2502.14831) | [snap-research/diffusability](https://github.com/snap-research/diffusability) |
| E2E-VAE (REPA-E) | REPA-E: Unlocking VAE for End-to-End Tuning with Latent Diffusion Transformers | [Paper](https://arxiv.org/abs/2504.10483) | [Project Page](https://end2end-diffusion.github.io/) |
| l-DeTok | Latent Denoising Makes Good Visual Tokenizers | [Paper](https://arxiv.org/abs/2507.15856) | [Jiawei-Yang/DeTok](https://github.com/Jiawei-Yang/DeTok) |

#### Discrete Tokenizers: Reconstruction Fidelity

§3.2.2 focuses on codebook scaling and utilization, stochastic quantization, gradient propagation, and implicit codebooks. Table 6 provides further discrete-tokenizer comparisons. UniWeTok is included here because §3.2.2 discusses it alongside WeTok for group-wise lookup-free quantization.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| VQ-VAE | Neural Discrete Representation Learning | [Paper](https://arxiv.org/abs/1711.00937) | - |
| VQGAN | Taming Transformers for High-Resolution Image Synthesis | [Paper](https://arxiv.org/abs/2012.09841) | [CompVis/taming-transformers](https://github.com/CompVis/taming-transformers) |
| SQ-VAE | SQ-VAE: Variational Bayes on Discrete Representation with Self-annealed Stochastic Quantization | [Paper](https://arxiv.org/abs/2205.07547) | - |
| FSQ | Finite Scalar Quantization: VQ-VAE Made Simple | [Paper](https://arxiv.org/abs/2309.15505) | [google-research/fsq](https://github.com/google-research/google-research/tree/master/fsq) |
| MAGVIT-v2 | Language Model Beats Diffusion -- Tokenizer is Key to Visual Generation | [Paper](https://arxiv.org/abs/2310.05737) | [Project Page](https://magvit.cs.cmu.edu/v2/) |
| LlamaGen | Autoregressive Model Beats Diffusion: Llama for Scalable Image Generation | [Paper](https://arxiv.org/abs/2406.06525) | [FoundationVision/LlamaGen](https://github.com/FoundationVision/LlamaGen) |
| BSQ | Image and Video Tokenization with Binary Spherical Quantization | [Paper](https://arxiv.org/abs/2406.07548) | [zhaoyue-zephyrus/bsq-vit](https://github.com/zhaoyue-zephyrus/bsq-vit) |
| VQGAN-LC | Scaling the Codebook Size of VQ-GAN to 100,000 with a Utilization Rate of 99% | [Paper](https://arxiv.org/abs/2406.11837) | - |
| Open-MAGVIT2 | Open-MAGVIT2: An Open-Source Project Toward Democratizing Auto-regressive Visual Generation | [Paper](https://arxiv.org/abs/2409.04410) | [TencentARC/SEED-Voken](https://github.com/TencentARC/SEED-Voken/blob/main/docs/Open-MAGVIT2.md) |
| SimVQ | Addressing Representation Collapse in Vector Quantized Models with One Linear Layer | [Paper](https://arxiv.org/abs/2411.02038) | [youngsheen/SimVQ](https://github.com/youngsheen/SimVQ) |
| IBQ | Scalable Image Tokenization with Index Backpropagation Quantization | [Paper](https://arxiv.org/abs/2412.02692) | [TencentARC/SEED-Voken](https://github.com/TencentARC/SEED-Voken/blob/main/docs/IBQ.md) |
| WeTok | WeTok: Powerful Discrete Tokenization for High-Fidelity Visual Reconstruction | [Paper](https://arxiv.org/abs/2508.05599) | [zhuangshaobin/WeTok](https://github.com/zhuangshaobin/WeTok) |
| FVQ | Scalable Training for Vector-Quantized Networks with 100% Codebook Utilization | [Paper](https://arxiv.org/abs/2509.10140) | - |
| UniWeTok | UniWeTok: An Unified Binary Tokenizer with Codebook Size 2<sup>128</sup> for Unified Multimodal Large Language Model | [Paper](https://arxiv.org/abs/2602.14178) | [shallowdream204/BitDance](https://github.com/shallowdream204/BitDance/blob/main/README_UniWeTok.md) |

Additional discrete tokenizer designs and quantization studies. AliTok aligns discrete tokens with autoregressive modeling; OmniTokenizer jointly handles images and videos. The two Wasserstein VQ papers describe related distributional-matching studies from 2025 and 2026.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| - | Vector Quantization-Based Regularization for Autoencoders | [Paper](https://arxiv.org/abs/1905.11062) | - |
| VQ-VAE-2 | Generating Diverse High-Fidelity Images with VQ-VAE-2 | [Paper](https://arxiv.org/abs/1906.00446) | - |
| HQ-AE | Hierarchical Quantized Autoencoders | [Paper](https://arxiv.org/abs/2002.08111) | - |
| Improved VQGAN | Vector-quantized Image Modeling with Improved VQGAN | [Paper](https://arxiv.org/abs/2110.04627) | - |
| MoVQ | MoVQ: Modulating Quantized Vectors for High-Fidelity Image Generation | [Paper](https://arxiv.org/abs/2209.09002) | - |
| MAGVIT | MAGVIT: Masked Generative Video Transformer | [Paper](https://arxiv.org/abs/2212.05199) | [Project Page](https://magvit.cs.cmu.edu/) |
| - | Designing a Better Asymmetric VQGAN for StableDiffusion | [Paper](https://arxiv.org/abs/2306.04632) | - |
| CVQ-VAE | Online Clustered Codebook | [Paper](https://arxiv.org/abs/2307.15139) | [lyndonzheng/CVQ-VAE](https://github.com/lyndonzheng/CVQ-VAE) |
| SCQ | Soft Convex Quantization: Revisiting Vector Quantization with Convex Optimization | [Paper](https://arxiv.org/abs/2310.03004) | - |
| Efficient-VQGAN | Efficient-VQGAN: Towards High-Resolution Image Generation with Efficient Vision Transformers | [Paper](https://arxiv.org/abs/2310.05400) | - |
| HQ-VAE | HQ-VAE: Hierarchical Discrete Representation Learning with Variational Bayes | [Paper](https://arxiv.org/abs/2401.00365) | - |
| LG-VQ | LG-VQ: Language-Guided Codebook Learning | [Paper](https://arxiv.org/abs/2405.14206) | - |
| OmniTokenizer | OmniTokenizer: A Joint Image-Video Tokenizer for Visual Generation | [Paper](https://arxiv.org/abs/2406.09399) | [FoundationVision/OmniTokenizer](https://github.com/FoundationVision/OmniTokenizer) |
| AliTok | AliTok: Towards Sequence Modeling Alignment between Tokenizer and Autoregressive Model | [Paper](https://arxiv.org/abs/2506.05289) | - |
| Wasserstein VQ (2025 study) | Enhancing Vector Quantization with Distributional Matching: A Theoretical and Empirical Study | [Paper](https://arxiv.org/abs/2506.15078) | [VQ-Research/Wasserstein-VQ](https://github.com/VQ-Research/Wasserstein-VQ) |
| Wasserstein VQ (2026 framework) | Distributional Matching for Vector Quantization: A Unified Theoretical and Empirical Framework | [Paper](https://arxiv.org/abs/2607.15933) | [VQ-Research/Wasserstein-VQ](https://github.com/VQ-Research/Wasserstein-VQ) |

#### Compression Efficiency

§3.2.3 distinguishes **per-token capacity** from **global compression**. PQ, RVQ, RQ-VAE, AQ, and VAR are grouped here according to that discussion. QINCo is also shown in Fig. 1.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| PQ | Product Quantization for Nearest Neighbor Search | [Paper](https://inria.hal.science/inria-00514462v1/document) | - |
| RVQ | Approximate Nearest Neighbor Search by Residual Vector Quantization | [Paper](https://www.mdpi.com/1424-8220/10/12/11259) | - |
| AQ | Additive Quantization for Extreme Vector Compression | [Paper](https://www.cv-foundation.org/openaccess/content_cvpr_2014/html/Babenko_Additive_Quantization_for_2014_CVPR_paper.html) | - |
| RQ-VAE | Autoregressive Image Generation using Residual Quantization | [Paper](https://arxiv.org/abs/2203.01941) | [kakaobrain/rq-vae-transformer](https://github.com/kakaobrain/rq-vae-transformer) |
| QINCo | Residual Quantization with Implicit Neural Codebooks | [Paper](https://arxiv.org/abs/2401.14732) | - |
| VAR | Visual Autoregressive Modeling: Scalable Image Generation via Next-Scale Prediction | [Paper](https://arxiv.org/abs/2404.02905) | [FoundationVision/VAR](https://github.com/FoundationVision/VAR) |

Global compression reduces spatial resolution or token count. The survey highlights DC-AE, DC-AE 1.5, and TiTok; the related works below extend this direction through compact, flexible, or optimized token sequences. SoftVQ-VAE uses continuous 1D tokens, while TiTok uses discrete 1D tokens.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| - | Bit Prioritization in Variational Autoencoders via Progressive Coding | [Paper](https://proceedings.mlr.press/v162/shu22a.html) | - |
| - | Subobject-level Image Tokenization | [Paper](https://arxiv.org/abs/2402.14327) | - |
| TiTok | An Image is Worth 32 Tokens for Reconstruction and Generation | [Paper](https://arxiv.org/abs/2406.07550) | [bytedance/1d-tokenizer](https://github.com/bytedance/1d-tokenizer) |
| DC-AE | Deep Compression Autoencoder for Efficient High-Resolution Diffusion Models | [Paper](https://arxiv.org/abs/2410.10733) | [mit-han-lab/efficientvit](https://github.com/mit-han-lab/efficientvit) |
| SoftVQ-VAE | SoftVQ-VAE: Efficient 1-Dimensional Continuous Tokenizer | [Paper](https://arxiv.org/abs/2412.10958) | [Hhhhhhao/continuous_tokenizer](https://github.com/Hhhhhhao/continuous_tokenizer) |
| FlexTok | FlexTok: Resampling Images into 1D Token Sequences of Flexible Length | [Paper](https://arxiv.org/abs/2502.13967) | [apple/ml-flextok](https://github.com/apple/ml-flextok) |
| token-opt | Highly Compressed Tokenizer Can Generate Without Training | [Paper](https://arxiv.org/abs/2506.08257) | [lukaslaobeyer/token-opt](https://github.com/lukaslaobeyer/token-opt) |
| DC-AE 1.5 | DC-AE 1.5: Accelerating Diffusion Model Convergence with Structured Latent Space | [Paper](https://arxiv.org/abs/2508.00413) | [dc-ai-projects/DC-Gen](https://github.com/dc-ai-projects/DC-Gen) |

#### Representation Disentanglement

§3.2.4 discusses information-capacity control, total-correlation penalties, and moment matching. These methods are separated from the reconstruction-fidelity group to reflect their principal objective.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| β-VAE | β-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework | [Paper](https://openreview.net/pdf?id=Sy2fzU9gl) | - |
| DIP-VAE | Variational Inference of Disentangled Latent Concepts from Unlabeled Observations | [Paper](https://arxiv.org/abs/1711.00848) | - |
| β-TCVAE | Isolating Sources of Disentanglement in Variational Autoencoders | [Paper](https://arxiv.org/abs/1802.04942) | - |
| FactorVAE | Disentangling by Factorising | [Paper](https://arxiv.org/abs/1802.05983) | - |
| - | Understanding Disentangling in β-VAE | [Paper](https://arxiv.org/abs/1804.03599) | - |
| ControlVAE | ControlVAE: Controllable Variational Autoencoder | [Paper](https://arxiv.org/abs/2004.05988) | [HuajieShao/ControlVAE-ICML2020](https://github.com/HuajieShao/ControlVAE-ICML2020) |
| DynamicVAE | DynamicVAE: Decoupling Reconstruction Error and Disentangled Representation Learning | [Paper](https://arxiv.org/abs/2009.06795) | - |

## Unified Tokenizers

[Survey §4](./paper/tokenizer_survey_project.pdf#page=15). Unified tokenizers combine high-level semantics and fine-grained visual information within a shared representation. The four architectural groups follow the method taxonomy in Tables 1–4. ImageFolder and VFMTok are listed in their corresponding unified groups.

### Single Encoder: Enhancing Semantics

§4.1.1 and Table 1. These methods start from reconstruction-oriented tokenization and add semantic supervision through distillation, language objectives, or visual self-supervised learning.

#### Semantic Distillation

Semantic features from pretrained models enrich the reconstructive token representation. Emu3.5 supplements this group from the single-encoder distillation comparisons in Table 9.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| VQ-KD | Image Understanding Makes for A Good Tokenizer for Image Generation | [Paper](https://arxiv.org/abs/2411.04406) | [magic-research/vector_quantization](https://github.com/magic-research/vector_quantization) |
| VA-VAE | Reconstruction vs. Generation: Taming Optimization Dilemma in Latent Diffusion Models | [Paper](https://arxiv.org/abs/2501.01423) | [hustvl/LightningDiT](https://github.com/hustvl/LightningDiT) |
| MAETok | Masked Autoencoders Are Effective Tokenizers for Diffusion Models | [Paper](https://arxiv.org/abs/2502.03444) | [Hhhhhhao/continuous_tokenizer](https://github.com/Hhhhhhao/continuous_tokenizer) |
| GigaTok | GigaTok: Scaling Visual Tokenizers to 3 Billion Parameters for Autoregressive Image Generation | [Paper](https://arxiv.org/abs/2504.08736) | [Project Page](https://silentview.github.io/GigaTok/) |
| Ming-Tok | Ming-UniVision: Joint Image Understanding and Generation with a Unified Continuous Tokenizer | [Paper](https://arxiv.org/abs/2510.06590) | [inclusionAI/Ming-UniVision](https://github.com/inclusionAI/Ming-UniVision) |
| Emu3.5 | Emu3.5: Native Multimodal Models are World Learners | [Paper](https://arxiv.org/abs/2510.26583) | [baaivision/Emu3.5](https://github.com/baaivision/Emu3.5) |
| GloTok | GloTok: Global Perspective Tokenizer for Image Reconstruction and Generation | [Paper](https://arxiv.org/abs/2511.14184) | - |
| RecTok | RecTok: Reconstruction Distillation along Rectified Flow | [Paper](https://arxiv.org/abs/2512.13421) | [Project Page](https://shi-qingyu.github.io/rectok.github.io/) |
| PyraTok | PyraTok: Language-Aligned Pyramidal Tokenizer for Video Understanding and Generation | [Paper](https://arxiv.org/abs/2601.16210) | - |

#### Language Supervision

Contrastive image-text alignment, captioning, or downstream language-model training provides semantic supervision.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| ImageFolder | ImageFolder: Autoregressive Image Generation with Folded Tokens | [Paper](https://arxiv.org/abs/2410.01756) | [Project Page](https://lxa9867.github.io/works/imagefolder/index.html) |
| UniTok | UniTok: A Unified Tokenizer for Visual Generation and Understanding | [Paper](https://arxiv.org/abs/2502.20321) | [FoundationVision/UniTok](https://github.com/FoundationVision/UniTok) |
| ETT | End-to-End Vision Tokenizer Tuning | [Paper](https://arxiv.org/abs/2505.10562) | - |
| AToken | AToken: A Unified Tokenizer for Vision | [Paper](https://arxiv.org/abs/2509.14476) | [apple/ml-atoken](https://github.com/apple/ml-atoken) |
| MANZANO | MANZANO: A Simple and Scalable Unified Multimodal Model with a Hybrid Vision Tokenizer | [Paper](https://arxiv.org/abs/2509.16197) | [Project Page](https://machinelearning.apple.com/research/manzano) |

#### Visual Self-Supervised Learning

VTP combines visual self-supervision with contrastive alignment and reconstruction, emphasizing scalable tokenizer pretraining.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| VTP | Towards Scalable Pre-training of Visual Tokenizers for Generation | [Paper](https://arxiv.org/abs/2512.13687) | [MiniMax-AI/VTP](https://github.com/MiniMax-AI/VTP) |

### Single Encoder: Preserving Semantics

§4.1.2 and Tables 2–3. These methods start from pretrained semantic encoders and add reconstruction capability while retaining the pretrained semantics.

#### Frozen Vision Foundation Models

A frozen semantic backbone is paired with a reconstruction decoder, sometimes using intermediate features to recover details. BLIP3-o supplements this group from Table 9; ILLUME is a related frozen-encoder method, classified by its original paper (Appendix A).

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| Emu2 | Generative Multimodal Models are In-Context Learners | [Paper](https://arxiv.org/abs/2312.13286) | [Project Page](https://baaivision.github.io/emu2/) |
| Divot | Divot: Diffusion Powers Video Tokenizer for Comprehension and Generation | [Paper](https://arxiv.org/abs/2412.04432) | [TencentARC/Divot](https://github.com/TencentARC/Divot) |
| ILLUME | ILLUME: Illuminating Your LLMs to See, Draw, and Self-Enhance | [Paper](https://arxiv.org/abs/2412.06673) | - |
| BLIP3-o | BLIP3-o: A Family of Fully Open Unified Multimodal Models-Architecture, Training and Dataset | [Paper](https://arxiv.org/abs/2505.09568) | [JiuhaiChen/BLIP3o](https://github.com/JiuhaiChen/BLIP3o) |
| VFMTok | Vision Foundation Models as Effective Visual Tokenizers for Autoregressive Image Generation | [Paper](https://arxiv.org/abs/2507.08441) | [CVMI-Lab/VFMTok](https://github.com/CVMI-Lab/VFMTok) |
| RAE | Diffusion Transformers with Representation Autoencoders | [Paper](https://arxiv.org/abs/2510.11690) | [Project Page](https://rae-dit.github.io/) |
| VFM-VAE | Vision Foundation Models Can Be Good Tokenizers for Latent Diffusion Models | [Paper](https://arxiv.org/abs/2510.18457) | [tianciB/VFM-VAE](https://github.com/tianciB/VFM-VAE) |
| DINO-Tok | DINO-Tok: Adapting DINO for Visual Tokenizers | [Paper](https://arxiv.org/abs/2511.20565) | [MKJia/DINO-Tok](https://github.com/MKJia/DINO-Tok) |
| FAE | One Layer Is Enough: Adapting Pretrained Visual Encoders for Image Generation | [Paper](https://arxiv.org/abs/2512.07829) | - |

#### Fine-Tuning Vision Foundation Models

Contrastive learning or self-distillation constrains semantic drift during reconstruction training. QLIP uses contrastive training followed by a frozen-encoder stage; it is listed here following Table 2.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| VILA-U | VILA-U: A Unified Foundation Model Integrating Visual Understanding and Generation | [Paper](https://arxiv.org/abs/2409.04429) | [mit-han-lab/vila-u](https://github.com/mit-han-lab/vila-u) |
| QLIP | QLIP: Text-Aligned Visual Tokenization Unifies Auto-Regressive Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2502.05178) | [NVlabs/QLIP](https://github.com/NVlabs/QLIP) |
| DualToken | DualToken: Towards Unifying Visual Understanding and Generation with Dual Visual Vocabularies | [Paper](https://arxiv.org/abs/2503.14324) | [songweii/DualToken](https://github.com/songweii/DualToken) |
| TA-Tok | Vision as a Dialect: Unifying Visual Understanding and Generation via Text-Aligned Representations | [Paper](https://arxiv.org/abs/2506.18898) | [Project Page](https://tar.csuhan.com/) |
| UniLIP | UniLiP: Adapting CLIP for Unified Multimodal Understanding, Generation and Editing | [Paper](https://arxiv.org/abs/2507.23278) | [nnnth/UniLIP](https://github.com/nnnth/UniLIP) |
| AVFM | Aligning Visual Foundation Encoders to Tokenizers for Diffusion Models | [Paper](https://arxiv.org/abs/2509.25162) | [Project Page](https://aligntok.github.io/) |
| UniFlow | UniFlow: A Unified Pixel Flow Tokenizer for Visual Understanding and Generation | [Paper](https://arxiv.org/abs/2510.10575) | [ZhengrongYue/UniFlow](https://github.com/ZhengrongYue/UniFlow) |
| VQRAE | VQRAE: Representation Quantization Autoencoders for Multimodal Understanding, Generation and Reconstruction | [Paper](https://arxiv.org/abs/2511.23386) | - |
| VGT | Visual Generation Tuning | [Paper](https://arxiv.org/abs/2511.23469) | [hustvl/VGT](https://github.com/hustvl/VGT) |
| UAE | The Prism Hypothesis: Harmonizing Semantic and Pixel Representations via Unified Autoencoding | [Paper](https://arxiv.org/abs/2512.19693) | [WeichenFan/UAE](https://github.com/WeichenFan/UAE) |
| DINO-SAE | DINO-SAE: DINO Spherical Autoencoder for High-Fidelity Image Reconstruction and Generation | [Paper](https://arxiv.org/abs/2601.22904) | [wkdgnsgo/dino-sae](https://github.com/wkdgnsgo/dino-sae) |

### Dual Encoder: Parallel

§4.2.1 and Table 4. Complementary encoded features are fused into shared tokens. Following the survey, this group also includes TA-TiTok's text-aware tokenization.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| MUSE-VL | Muse-VL: Modeling Unified VLM through Semantic Discrete Encoding | [Paper](https://arxiv.org/abs/2411.17762) | - |
| TokenFlow | TokenFlow: Unified Image Tokenizer for Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2412.03069) | [ByteVisionLab/TokenFlow](https://github.com/ByteVisionLab/TokenFlow) |
| TA-TiTok | Democratizing Text-to-Image Masked Generative Models with Compact Text-Aware One-Dimensional Tokens | [Paper](https://arxiv.org/abs/2501.07730) | [bytedance/1d-tokenizer](https://github.com/bytedance/1d-tokenizer) |
| SemHiTok | SemHiTok: A Unified Image Tokenizer via Semantic-Guided Hierarchical Codebook for Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2503.06764) | - |
| ILLUME+ | ILLUME+: Illuminating Unified MLLM with Dual Visual Tokenization and Diffusion Refinement | [Paper](https://arxiv.org/abs/2504.01934) | [illume-unified-mllm/ILLUME_plus](https://github.com/illume-unified-mllm/ILLUME_plus) |
| UniToken | UniToken: Harmonizing Multimodal Understanding and Generation through Unified Visual Encoding | [Paper](https://arxiv.org/abs/2504.04423) | [SxJyJay/UniToken](https://github.com/SxJyJay/UniToken) |
| Show-o2 | Show-o2: Improved Native Unified Multimodal Models | [Paper](https://arxiv.org/abs/2506.15564) | [showlab/Show-o](https://github.com/showlab/Show-o) |
| SVGTok | Latent Diffusion Model without Variational Autoencoder | [Paper](https://arxiv.org/abs/2510.15301) | [shiml20/SVG](https://github.com/shiml20/SVG) |
| EMMA | EMMA: Efficient Multimodal Understanding, Generation, and Editing with a Unified Architecture | [Paper](https://arxiv.org/abs/2512.04810) | [umm-emma/emma](https://github.com/umm-emma/emma) |

### Dual Encoder: Cascade

§4.2.2 and Table 4. One encoder operates on features produced by another, progressively combining semantic abstraction and visual detail. The cascade can learn semantics over low-level features or compress high-level features with an autoencoder.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| USP | USP: Unified Self-Supervised Pretraining for Image Generation and Understanding | [Paper](https://arxiv.org/abs/2503.06132) | [AMAP-ML/USP](https://github.com/AMAP-ML/USP) |
| Harmon | Harmonizing Visual Representations for Unified Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2503.21979) | [wusize/Harmon](https://github.com/wusize/Harmon) |
| TokLIP | TokLIP: Marry Visual Tokens to CLIP for Multimodal Comprehension and Generation | [Paper](https://arxiv.org/abs/2505.05422) | [TencentARC/TokLIP](https://github.com/TencentARC/TokLIP) |
| TUNA | TUNA: Taming Unified Visual Representations for Native Unified Multimodal Models | [Paper](https://arxiv.org/abs/2512.02014) | [Project Page](https://tuna-ai.org/) |
| PS-VAE | Both Semantics and Reconstruction Matter: Making Representation Encoders Ready for Text-to-Image Generation and Editing | [Paper](https://arxiv.org/abs/2512.17909) | [Project Page](https://jshilong.github.io/PS-VAE-PAGE/) |
| OpenVision 3 | OpenVision 3: A Family of Unified Visual Encoder for Both Understanding and Generation | [Paper](https://arxiv.org/abs/2601.15369) | [UCSC-VLAA/OpenVision](https://github.com/UCSC-VLAA/OpenVision) |

MANZANO follows the single-encoder assignment in §4.1.1/Table 1, and PS-VAE follows the cascade assignment in §4.2.2/Table 4. Their placements in the multimodal benchmark table (Table 9) differ from those architectural assignments.

## Unified Multimodal Systems Using Task-Specific Tokenizers

[Survey §5.3 and Table 9](./paper/tokenizer_survey_project.pdf#page=25). These systems support both understanding and generation at the model level while using task-specific visual tokenizers. They are grouped by the tokenizer strategy reported in the survey.

### One Task-Specific Visual Tokenizer

A single reconstruction-oriented tokenizer supplies visual tokens to the multimodal model. Examples include VQGAN in LWM, SD-VAE in Transfusion, and MAGVIT-v2 in Show-o and MMaDA.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| LWM | World Model on Million-Length Video And Language With Blockwise RingAttention | [Paper](https://arxiv.org/abs/2402.08268) | [Project Page](https://largeworldmodel.github.io/lwm/) |
| Transfusion | Transfusion: Predict the Next Token and Diffuse Images with One Multi-Modal Model | [Paper](https://arxiv.org/abs/2408.11039) | - |
| Show-o | Show-o: One Single Transformer to Unify Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2408.12528) | [showlab/Show-o](https://github.com/showlab/Show-o) |
| Emu3 | Emu3: Next-Token Prediction is All You Need | [Paper](https://arxiv.org/abs/2409.18869) | [baaivision/Emu3](https://github.com/baaivision/Emu3) |
| D-DiT | Dual Diffusion for Unified Image Generation and Understanding | [Paper](https://arxiv.org/abs/2501.00289) | - |
| MMaDA | MMaDA: Multimodal Large Diffusion Language Models | [Paper](https://arxiv.org/abs/2505.15809) | [Gen-Verse/MMaDA](https://github.com/Gen-Verse/MMaDA) |
| Muddit | Muddit: Liberating Generation Beyond Text-to-Image with a Unified Discrete Diffusion Model | [Paper](https://arxiv.org/abs/2505.23606) | [M-E-AGI-Lab/Muddit](https://github.com/M-E-AGI-Lab/Muddit) |
| Lumina-DiMOO | Lumina-DiMOO: An Omni Diffusion Large Language Model for Multi-Modal Generation and Understanding | [Paper](https://arxiv.org/abs/2510.06308) | [Alpha-VLLM/Lumina-DiMOO](https://github.com/Alpha-VLLM/Lumina-DiMOO) |

### Separate Task-Specific Visual Tokenizers

Perception and generation use distinct visual representations, such as SigLIP plus VQ in Janus or SigLIP2 plus VAE in BAGEL. §4.2.1 discusses these systems as motivation for learning shared representations.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| Unified-IO 2 | Unified-IO 2: Scaling Autoregressive Multimodal Models with Vision, Language, Audio, and Action | [Paper](https://arxiv.org/abs/2312.17172) | [allenai/unified-io-2](https://github.com/allenai/unified-io-2) |
| Janus | Janus: Decoupling Visual Encoding for Unified Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2410.13848) | [deepseek-ai/Janus](https://github.com/deepseek-ai/Janus) |
| JanusFlow | JanusFlow: Harmonizing Autoregression and Rectified Flow for Unified Multimodal Understanding and Generation | [Paper](https://arxiv.org/abs/2411.07975) | [deepseek-ai/Janus](https://github.com/deepseek-ai/Janus) |
| Janus-Pro | Janus-Pro: Unified Multimodal Understanding and Generation with Data and Model Scaling | [Paper](https://arxiv.org/abs/2501.17811) | [deepseek-ai/Janus](https://github.com/deepseek-ai/Janus) |
| UniFluid | Unified Autoregressive Visual Generation and Understanding with Continuous Tokens | [Paper](https://arxiv.org/abs/2503.13436) | - |
| MindOmni | MindOmni: Unleashing Reasoning Generation in Vision Language Models with RGPO | [Paper](https://arxiv.org/abs/2505.13031) | - |
| BAGEL | Emerging Properties in Unified Multimodal Pretraining | [Paper](https://arxiv.org/abs/2505.14683) | [bytedance-seed/BAGEL](https://github.com/bytedance-seed/BAGEL) |
| Skywork UniPic | Skywork UniPic: Unified Autoregressive Modeling for Visual Understanding and Generation | [Paper](https://arxiv.org/abs/2508.03320) | - |

## Task and Modality Extensions

The survey also discusses video encoding (§2) and dynamic/adaptive tokenization (§6). The following references are organized by those themes; the survey does not assign them to the four detailed unified-tokenizer architecture groups.

### Video and Universal Visual Encoding

VTok models shared spatial and motion tokens for video understanding and generation. HUVR uses implicit neural representations for image encoding with pixel reconstruction and semantic distillation.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| HUVR | Implicit Neural Representation Facilitates Unified Universal Vision Encoding | [Paper](https://arxiv.org/abs/2601.14256) | [tiktok/huvr](https://github.com/tiktok/huvr) |
| VTok | VTok: A Unified Video Tokenizer with Decoupled Spatial-Temporal Latents | [Paper](https://arxiv.org/abs/2602.04202) | [wangf3014/VTok](https://github.com/wangf3014/VTok) |

### Dynamic and Adaptive Tokenization

ALIT allocates variable-length tokens recurrently. DeRA uses discrete appearance/motion tokens with representation alignment. DCS-Tok, the continuous tokenizer in DCS-LDM, applies hierarchical compression across image/video scales. These methods are discussed in §6; compact tokenization methods already listed above are also relevant to that discussion.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| ALIT | Adaptive Length Image Tokenization via Recurrent Allocation | [Paper](https://arxiv.org/abs/2411.02393) | [ShivamDuggal4/adaptive-length-tokenizer](https://github.com/ShivamDuggal4/adaptive-length-tokenizer) |
| DCS-Tok (DCS-LDM) | Decoupling Complexity from Scale in Latent Diffusion Model | [Paper](https://arxiv.org/abs/2511.16117) | - |
| DeRA | DeRA: Decoupled Representation Alignment for Video Tokenization | [Paper](https://arxiv.org/abs/2512.04483) | - |

### Masks and Structured Visual Outputs

SAMTok tokenizes masks into compact residual-quantized codes for region understanding and segmentation; it is also discussed in §6. All in Tokens studies a shared tokenized output space for visual tasks.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| - | All in Tokens: Unifying Output Space of Visual Tasks via Soft Token | [Paper](https://arxiv.org/abs/2301.02229) | - |
| SAMTok | SAMTok: Representing Any Mask with Two Words | [Paper](https://arxiv.org/abs/2601.16093) | [Project Page](https://zhouyiks.github.io/projects/SAMTok/) |

## Related Generation and Background References

These papers provide generation, alignment, or inference context for the tokenizer literature.

### Generation Models and Representation Alignment

Generative modeling and training studies using visual latents or discrete tokens. REPA aligns representations during diffusion-transformer training; the autoencoder-tuning method REPA-E is listed with continuous tokenizers above.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| VQ-Diffusion | Vector Quantized Diffusion Model for Text-to-Image Synthesis | [Paper](https://arxiv.org/abs/2111.14822) | - |
| MaskGIT | MaskGIT: Masked Generative Image Transformer | [Paper](https://arxiv.org/abs/2202.04200) | [google-research/maskgit](https://github.com/google-research/maskgit) |
| Emu (image generation) | Emu: Enhancing Image Generation Models Using Photogenic Needles in a Haystack | [Paper](https://arxiv.org/abs/2309.15807) | - |
| MAR | Autoregressive Image Generation without Vector Quantization | [Paper](https://arxiv.org/abs/2406.11838) | [LTH14/mar](https://github.com/LTH14/mar) |
| REPA | Representation Alignment for Generation: Training Diffusion Transformers Is Easier Than You Think | [Paper](https://arxiv.org/abs/2410.06940) | [sihyun-yu/REPA](https://github.com/sihyun-yu/REPA) |
| Meissonic | Meissonic: Revitalizing Masked Generative Transformers for Efficient High-Resolution Text-to-Image Synthesis | [Paper](https://arxiv.org/abs/2410.08261) | [viiika/Meissonic](https://github.com/viiika/Meissonic) |
| Fluid | Fluid: Scaling Autoregressive Text-to-Image Generative Models with Continuous Tokens | [Paper](https://arxiv.org/abs/2410.13863) | - |

### Inference and Training Foundations

Foundational inference, distillation, and posterior-collapse studies. Generating Sentences from a Continuous Space is an NLP reference relevant to continuous latent modeling.

| Alias | Paper | Link | Code / Project |
| --- | --- | --- | --- |
| Knowledge Distillation | Distilling the Knowledge in a Neural Network | [Paper](https://arxiv.org/abs/1503.02531) | - |
| - | Variational Inference with Normalizing Flows | [Paper](https://arxiv.org/abs/1505.05770) | - |
| - | Generating Sentences from a Continuous Space | [Paper](https://arxiv.org/abs/1511.06349) | - |
| - | Cyclical Annealing Schedule: A Simple Approach to Mitigating KL Vanishing | [Paper](https://arxiv.org/abs/1903.10145) | - |
| - | Automatic Variational Inference with Cascading Flows | [Paper](https://arxiv.org/abs/2102.04801) | - |

## Citation

If you find this survey or repository useful, please consider citing:

```bibtex
@article{shi2026visual,
  author    = {Shi, Qingyu and Yuan, Haobo and Zhou, Yikang and Li, Xiu and Li, Jason and Wu, Size and Wang, Haochen and Tian, Ye and Zhang, Tao and Bai, Jinbin and Wang, Yujing and Qi, Lu and Tong, Yunhai and Yang, Ming-Hsuan},
  title     = {Visual Tokenizers: A Comprehensive Survey},
  journal   = {Technical Report},
  year      = {2026}
}
```
