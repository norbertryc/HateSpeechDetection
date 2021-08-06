# HateSpeechDetection
Hate spech detection experiments for polish language

Repository contains experiments about hate sppech classification and usage instruction for depoloyed system based on this experiments.

Repository structure:
- `establishing_baseline.ipynb` - provides experiments about baseline models.
- `data_preprocessing.ipynb` - provides code for data preparation. 


# Experiments

 Main tested factors:
  - text lemmatized or raw
  - Document Term Matrix or TFIDF matrix as text representation (and their hiperparameters)
  - dimensionality reduction with SVD
  - naive Bayes and linear SVM classifiers (and their hiperparameters)
  
 Main evaluation metric considered: Micro F1 Score (because of high class imbalance)

# Deployed prototype

System performs "hate speech" classification - assigns to text one of three possible classes:
 - 0: non-harmful
 - 1: cyberbullying
 - 2: hate-speech
 
## Usage
1. Download dokcer image: `docker pull norbertryc/hate_speech:hsc`

2. Run docker image: `docker run -p 7777:7777 hate\_speech\_classification`

3. Call url in browser: `http://172.17.0.2:7777/predict?text=<text to classify>`

### Example usage

`http://172.17.0.2:7777/predict?text=jest fajnie` -> prediction = class 0

`172.17.0.2:7777/predict?text=@anonymized_account%20Nie%20bucz,%20i%20tak%20%C5%9Bmierdzisz` -> prediction = class 2

Text can be provided in a natural way - with polish characters and spaces.

### Additional info
Image size: 681 MB
