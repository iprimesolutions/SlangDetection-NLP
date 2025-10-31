# SlangDetection-NLP
A project work on Cloud Machine Learning


# Rational and Scope
We may use Amazon S3, Amazon Transcribe, and Amazon Comprehend to manage various pipeline steps in order to develop a slang detection system. Our storage solution will be Amazon S3, to which we will upload audio recordings that comprise natural speech. Amazon Transcribe will be used to process these audio files, turning the spoken content into text.
Amazon Comprehend, a natural language processing (NLP) tool that can recognize entities, important phrases, and sentiment, can then be used to examine the generated transcriptions. We will concentrate on identifying slang phrases and colloquial expressions that might differ depending on the location, the population, or the situation by utilizing Comprehend's custom classification features.
Using linguistic attributes taken from the transcription, we may use the transcribed text to train a bespoke natural language processing model to categorize slang terms. The goal of this project is to create a scalable, automated slang identification system that uses real-world audio data by integrating AWS services. The finished model supports use cases in moderation, language comprehension, and cultural study by assisting in the identification and classification of slang usage

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/aa08120d-b149-4cd9-9533-a7f6a1ecd3ac" />

<img width="654" height="257" alt="image" src="https://github.com/user-attachments/assets/9df16ced-4b80-434e-8033-0515816eaf1b" />

<img width="1066" height="889" alt="image" src="https://github.com/user-attachments/assets/ed8a6084-07eb-4942-8a89-acd1db69fbca" />


# command to train the model
curl -X POST http://127.0.0.1:8000/slang/train \
  -H "Content-Type: application/json" \
  -d '{
    "s3Path": "s3://1cent301278686/custom-slangs/",
    "roleArn": "arn:aws:iam::985539802541:role/ComprehendSlangTrainerRole",
    "modelName": "SlangDetectorV8"
}'


# For implementation
Create an endpoint , then update the slang_detection_service.py to reflect the endpoint as below
response = comprehend.detect_entities(
    Text=text,
    LanguageCode="en",
    EndpointArn="arn:aws:comprehend:us-east-1:YOUR_ACCOUNT_ID:entity-recognizer-endpoint/slang-endpoint"
)
