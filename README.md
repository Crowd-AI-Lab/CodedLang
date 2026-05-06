# "Newspaper Eat" Means "Not Tasty": A Taxonomy and Benchmark for Coded Language in Real-World Chinese Online Reviews 
This repository provides datasets and code for the ACL 2026 long paper on Coded Language. 

> ["Newspaper Eat" Means "Not Tasty": A Taxonomy and Benchmark for Coded Language in Real-World Chinese Online Reviews](https://arxiv.org/abs/2601.19932  ) <br>
> [Ruyuan Wan](https://ruyuanwan.github.io/), [Changye Li](https://changyeli.github.io/$0), [Ting-Hao 'Kenneth' Huang](https://crowd.ist.psu.edu) <br>
> [ACL 2026]() <br>

## Overview

<p align="center">
  <img src="https://github.com/Crowd-AI-Lab/CodedLang/blob/main/CodedLang_Concept.png" width="80%">
</p>
<p align="center">
  Example of creative coded language in a Google Maps restaurant review. <br>
    Top: the original user review in Chinese, as posted on Google Maps. <br>
    Left: the machine-generated English translation produced by Google Translate. <br>
    Right: the inferred underlying meaning obtained by decoding phonetic substitutions.
</p>

## CodedLang Dataset
We introduce CodedLang, a dataset of 7,744 Chinese Google Maps reviews, including 900 reviews with span-level annotations of coded language.

🤗 Hugging Face Dataset: [https://huggingface.co/datasets/RuyuanWan/CodedLang ](https://huggingface.co/datasets/RuyuanWan/CodedLang)

### Taxonomy

We define 7 categories of coded language:

- **Ambiguous Homophones**  
- **Non-Lexical Homophones**  
- **Phonetic Substitution**  
- **Emoji Substitution**  
- **Orthographic Substitution**  
- **Cross-Lingual Phonetic Encoding**  
- **Cipher**  

### Data Sources

Our dataset is constructed based on two large-scale Google Maps review datasets:

- [Google Local Reviews (Li et al., 2022, Yan et al., 2023)](https://cseweb.ucsd.edu/~jmcauley/datasets.html#google_local  ): 666 million reviews  
- [Google Restaurant Reviews (Yan et al., 2023)](https://cseweb.ucsd.edu/~jmcauley/datasets.html#google_restaurants  ): 1.77 million reviews  

### Annotations

Each sample includes:
- `id`: Index of the review  
- `original_review`: Original Chinese review text  
- `translated_review`: English translation of the original review  
  - Note: 309 reviews are missing translations from the raw Google Reviews dataset and are kept as-is  
- `rating`: Review rating (1–5 stars)  
- `char_mask_review`: Character-level masked version of the review  
- `span_mask_review`: Span-level masked version of the review 
- `decode_review`: Decoded version of the review, where coded language is replaced with the intended meaning.   
- `coded_lang_class`: Taxonomy label(s) for coded language classes  
- `code_span`: Text span of coded expressions  
- `coded_language`: Binary label  
  - `1`: contains coded language  
  - `0`: non-coded review  

## Coded Language Dictionary

We provide a coded language dictionary derived from human annotations:

### Dictionary Fields

Each entry includes:
- `code_span`: Coded expression  
- `decode`: Normalized (decoded) form  
- `coded_lang_class`: Corresponding coded language category

For phonetic-based coded language, we additionally provide:
- `mid_homophone`: Intermediate homophone form (if applicable)  
- `code_pinyin`: Pinyin of the coded expression  
- `decode_pinyin`: Pinyin of the decoded expression  
- `code_ipa`: IPA representation of the coded expression  
- `decode_ipa`: IPA representation of the decoded expression  

## Benchmark Results
We evaluate language models on taxonomy-aware coded language classification.

<p align="center">
  <img src="https://github.com/Crowd-AI-Lab/CodedLang/blob/main/classification_results.png" width="60%">
</p>

<p align="center">
Coded language classification performance across models.
</p>

Results show substantial performance variation across coded language categories, with and cross-lingual transformations remaining particularly challenging for current language models.
For full benchmark results and analyses, please refer to the paper.

---
## Citation
If you find this work useful for your research, please cite our paper:

```
@inproceedings{wan2026newspaper,
  title={"Newspaper Eat" Means "Not Tasty": A Taxonomy and Benchmark for Coded Languages in Real-World Chinese Online Reviews},
  author={Wan, Ruyuan and Li, Changye and Huang, Ting-Hao'Kenneth'},
  booktitle={The 64th Annual Meeting of the Association for Computational Linguistics},
  year={2026}
}
```
