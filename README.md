# Xsum-FlanT5

Overview

This project focuses on fine-tuning the google/flan-t5-large model for generating news summaries using the XSum dataset. The fine-tuning process leverages the Parameter-Efficient Fine-Tuning (PEFT) approach with LoRA configuration to optimize computational resources while maintaining high performance. Due to resource constraints, the model was fine-tuned on a subset of 10,000 training samples from the XSum dataset.

The project includes data preprocessing, model fine-tuning, and inference to generate summaries, with results saved in a pandas DataFrame.

# Key features





Dataset: XSum dataset for news article summarization.



Model: google/flan-t5-large, fine-tuned with LoRA for efficiency.



Fine-Tuning: Uses PEFT with LoRA configuration to reduce computational requirements.



Inference: Generates summaries for test samples and stores results in a DataFrame.

Dataset

The project uses the XSum dataset, which contains news articles and their corresponding one-sentence summaries. Due to computational constraints, a subset of the dataset is used:





Training: 10,000 samples from the XSum training set.



Testing: 100 samples from the XSum test set.

The dataset is tokenized using the flan-t5-large tokenizer, with a maximum source length of 512 tokens and a maximum target length of 39 tokens (based on the 85th and 90th percentiles of input and target lengths, respectively).




Setup





Clone the Repository (if applicable):

git clone https://github.com/parisa-kavian/Xsum-FlanT5.git
cd Xsum-FlanT5



Install Dependencies: Create a requirements.txt file with the content above and run:

pip install -r requirements.txt



Environment:





The code is designed to run in environments like Google Colab with GPU support.



Ensure CUDA is installed if running locally for bitsandbytes and fp16 support.

