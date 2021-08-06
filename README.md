# HateSpeechDetection
Hate spech detection experiments for polish language

Repository contains experiments about hate sppech classification and usage instruction for depoloyed system based on this experiments.

Repository structure:
- `data_preprocessing.ipynb` - code for data preparation. 
- `establishing_baseline.ipynb` - experiments about baseline simple machine learning models.
- `transformers_baseline.ipynb` - experiments with using pretrained BERT-based encoder for text
- `evaluation.ipynb` - evaluation of best variant for each approach - quality and prediction speed



# Experiments

 Main tested factors in `establishing_baseline`:
  - text lemmatized or raw
  - Document Term Matrix or TFIDF matrix as text representation (and their hiperparameters)
  - dimensionality reduction with SVD
  - naive Bayes and linear SVM classifiers (and their hiperparameters)
  
 Experiments in `transformers_baseline`:
  - roberta model used as encoder (RoBERTa‑v2 (base) v4.4 from https://github.com/sdadas/polish-roberta)
  - linear svm and Multilayer Perceptron fitted and on the top of encodings optimized as classifiers
  
 Main evaluation metric considered: Micro F1 Score (because of high class imbalance)

# Results


| Model name   |      score [Micro F1]      |  Prediction speed [s/observation] |
|----------|:-------------:|------:|
| classic_ml |  0.879 | 0.000011 |
| transformer\_encoder\_based |    0.865  |   0.029091 |
    
# Deployed prototype

System performs "hate speech" classification - assigns to text one of three possible classes:
 - 0: non-harmful
 - 1: cyberbullying
 - 2: hate-speech
 
## Usage
1. Download dokcer image: `docker pull norbertryc/hate_speech:hsc`

2. Run docker image: `docker run -p 7777:7777 norbertryc/hate_speech:hsc`

3. Call url in browser: `localhost:7777/predict?text=<text to classify>`

### Example usage

`localhost:7777/predict?text=jest fajnie` -> prediction = class 0

`localhost:7777/predict?text=@anonymized_account%20Nie%20bucz,%20i%20tak%20%C5%9Bmierdzisz` -> prediction = class 2

Text can be provided in a natural way - with polish characters and spaces.



