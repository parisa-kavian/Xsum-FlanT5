This project focuses on summarizing news articles using the google/flan-t5-large model and the XSum dataset. To optimize the process and reduce the need for computational resources, the model was fine-tuned using the innovative Parameter-Efficient Fine-Tuning (PEFT) approach with the LoRA technique. Due to resource constraints, the fine-tuning process was conducted on a subset of 10,000 samples from the XSum training set.

The final output of the project includes generated summaries for the test data, which are stored in a pandas DataFrame.

### Key Features
* ** Dataset:** Utilizes the well-regarded XSum dataset for the news summarization task.

* **Model:** Leverages the powerful google/flan-t5-large model.

* ** Efficient Fine-Tuning:** Employs PEFT and LoRA to significantly reduce computational and memory costs.

* ** Inference:** Capable of generating summaries for new samples and storing the results in a DataFrame.

### 📊 Dataset
This project uses the XSum dataset, which contains news articles and their corresponding single-sentence summaries. Due to computational limitations, a subset of the dataset was used:

* ** Training:** 10,000 samples from the XSum training set.

* ** Testing:** 100 samples from the XSum test set.

The data has been processed with the flan-t5-large tokenizer. The maximum length for the input text is set to 512 tokens, and for the output summary, it is 39 tokens.

###⚙️ Setup
Follow these steps to run the project.

** Clone the Repository:**

```Bash

git clone https://github.com/parisa-kavian/Xsum-FlanT5.git
cd Xsum-FlanT5
```
** Install Dependencies:**
First, create a requirements.txt file with the content, then run the installation command.
```
pip install -r requirements.txt
```
