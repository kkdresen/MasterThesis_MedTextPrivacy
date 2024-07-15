# Master Thesis

This repository contains the code for my master thesis: *Balancing Privacy and Utility in Medical Text Data: PII Redaction and Differential Privacy. The Energy Cost of Developing GDPR-Compliant Text Anonymization Techniques*. All files should have sufficient documentation for reproduction and understanding. Any remaining questions or comments may be raised via an issue in this repository or sent to my e-mail.

## Abstract

There is a critical need to facilitate learning from medical data, yet there are major privacy concerns, this requires that we investigate and compare methods that enable its safe and secure use. Previous research has not compared Privacy-Enhancing Technologies (PETs) for text data to address direct and inferential privacy risks, utility, fidelity, and energy costs.

In this study, we develop a framework to integrate and evaluate GDPR-compliant anonymization methods, focusing on Named Entity Recognition (NER) for Personally Identifiable Information (PII) redaction and differentially private (DP) synthetic text generation, compared to a non-anonymized baseline. A data set of 2,016 patient-doctor transcriptions is compiled, revealing sensitive information.

Our findings show that NER-based PII redaction consistently outperforms DP synthetic text in terms of utility and fidelity, with a 25% increase in accuracy and ±0.40 increase in cosine similarity score, respectively. While DP methods enhance privacy, they significantly reduce data quality and increase energy consumption compared to the NER-driven method, using ±1600% more energy. By comparing these techniques, we provide insights into the impact on data utility and privacy, emphasizing the importance of energy-efficient methods in data processing. This study advances the field by integrating advanced NLP techniques, optimizing hyperparameters for DP synthetic data generation, and measuring energy costs, in a GDPR-compliant context, and can be easily extended beyond the medical domain.

## Structure of Repository

The repository has eight folders:

### Data
This folder contains the original dataset mtsamples.csv dataset and the preprocessed file `2016r_mtsamples_final.csv` containing extracted sentences of 2,016 patient-doctor transcriptions used in this study.

### EDA
This folder contains all code and Jupyter notebooks for the exploratory data analysis and data preprocessing.

### Medical PII Redaction
This folder contains all code and Jupyter notebooks for the experiments on Named Entity Recognition (NER) for Personally Identifiable Information (PII) redaction and energy measurement using CodeCarbon.

### DP Synthetic Data Generation
This folder contains all code and Jupyter notebooks for the experiments related to differentially private synthetic text generation using DistilGPT2. The code also includes the energy measurement of the anonymization technique using CodeCarbon and Renyi Differential Privacy to measure and validate the amount of noise added in the training process 

### Privacy
This folder contains all code and Jupyter notebooks related to assessing privacy using n-grams.

### Utility
This folder contains all code and Jupyter notebooks for evaluating the utility of the anonymized data using a multi-label classification task

### Fidelity
This folder contains all code and Jupyter notebooks for evaluating the fidelity of the anonymized data using cosine similarity.

### Validation Dataset: SST2
This folder contains all code and Jupyter notebooks for the experiments involving the SST2 dataset.

## Reproducing the Results

To reproduce the results, you need to use at least Python version 3.9 or later.

Start by preprocessing the original dataset to retrieve `2016r_mtsamples_final.csv`. Perform PII masking with the notebook found in the Medical PII Redaction folder. To fine-tune DistilGPT2, the notebooks for fine-tuning with different epsilon levels (to set the privacy budget) and for performing inference with various temperature and top-k levels are available in the DP Synthetic Data Generation folder.

To analyze fidelity using cosine similarity the notebook `Fidelity.ipynb` can be used. This can be found in the Fidelity folder.

To analyze privacy using n-grams the notebook `Privacy_Ngram.ipynb` can be used. This can be found in the Privacy folder. Privacy measurements through Renyi Differential Privacy (RDP) are directly integrated into the code found in `Medical_finetune.ipynb`.

To analyze utility using a multi-label classification task the notebook `Utility_MultiLabel_Classification.ipynb` can be used. This can be found in the Utility folder. In the experiment classifiers are trained on different anonymized datasets (e.g. DP Synthetic or Medical PII Redacted Text) and tested on the original test set.

The original SST2 validation dataset, the cleaning file to reduce the CSV to the same size, and the synthesized data can be found in the SST2 folder.



