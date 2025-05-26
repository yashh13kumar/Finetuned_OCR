TrOCR Fine-Tuning on Imgur5K Handwriting Dataset
This repository contains a complete pipeline to fine-tune Microsoft's TrOCR model on the Imgur5K Handwritten Dataset. The goal is to develop a robust OCR model capable of reading handwritten text snippets.

Features
✅ Fine-tuning on real handwritten data (TFRecords format)

✅ Data parsing and cleaning (punctuation, casing, noise removal)

✅ Data augmentation with affine/perspective/blur/color jitter

✅ TrOCR model from Hugging Face Transformers

✅ Character Error Rate (CER) and Exact Match Accuracy evaluation

✅ Early stopping + model saving + inference visualization

Dataset
Source: Imgur5K-Cropped TFRecords (Kaggle)

Format: .tfrecord

Fields extracted:

image: PNG bytes (converted to RGB)

label: UTF-8 text annotation

🔧 Requirements
bash
Copy
Edit
pip install kagglehub kaggle transformers sentencepiece evaluate jiwer datasets accelerate matplotlib protobuf==3.20.1 tensorboard


Base model: microsoft/trocr-small-handwritten

Batch size: 8

Epochs: 10 (early stopping enabled)

Learning rate: 3e-4

Evaluation: CER (Character Error Rate) and Exact Match Accuracy

📉 Sample Results
Epoch	Train Loss	Val Loss	CER	Accuracy
1	0.7749	0.1998	0.9545	-
5	0.0666	0.0847	0.3370	65–70%*

Exact match accuracy is calculated manually and also shown during inference visualizations.

🧾 Inference Example

img = Image.open("cropped_imgs/img_150.png")
ocr_text = ocr(img, processor, model)
print("Predicted:", ocr_text)
📊 Metrics
CER (Character Error Rate) → Lower is better

Exact Match Accuracy → Based on literal string matches (case-normalized, whitespace-trimmed)

