# HateSpeechDetection
Hate spech detection experiments for polish language

System performs "hate speech" classification - assigns to text on of three possible classes:
 - 0: non-harmful
 - 1: cyberbullying
 - 2: hate-speech
 
## Usage
1. Download dokcer image: `docker pull norbertryc/hate_speech:hsc`

2. Run docker image: `docker run -p 7777:7777 hate\_speech\_classification`

3. Call url in browser: `http://172.17.0.2:7777/predict?text=<text to classify>`

### Example usage

`http://172.17.0.2:7777/predict?text=fajnjest%20fajnie` -> prediction = class 0

`172.17.0.2:7777/predict?text=@anonymized_account%20Nie%20bucz,%20i%20tak%20%C5%9Bmierdzisz` -> prediction = class 2

### Additional info
Image size: 681 MB
