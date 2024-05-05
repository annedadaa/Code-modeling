# Improving LLMs on underrepresented programming languages: Phi-1.5 model fine-tuned on Kotlin 

All the code was written in Python notebooks so there's no specific instruction on how to run them. The code is commented and it's more self-explained, here I introduce the main information.

### Dataset

Kotlin code dataset was collected from the [kotlinx.coroutines](https://github.com/Kotlin/kotlinx.coroutines.git) repository. The code for collecting the dataset is located in the _Code/Dataset_preprocessing/_ folder. In total, 1049 Kotlin files were collected, and 100 of them were used to evaluate the model.

Python test set of the CodeXGLUE dataset was taken from the [CodeXGLUE repository](https://github.com/microsoft/CodeXGLUE/blob/main/Code-Code/CodeCompletion-line/dataset/py150/line_completion/test.json) and was used to evaluate the model. For comparability with the Kotlin test set, I took 100 samples of Python code, and each last line was taken as the target line that needs to be predicted. The code for Python data preprocessing is also available in the _Code/Dataset_preprocessing/_ folder.

### Evaluation

The code used for evaluation is located in the _Code_/_Evaluate_ folder. I used [Phi-1.5 model](https://huggingface.co/microsoft/phi-1_5) to predict the next code lines for both Python and Kotlin datasets. Files with predictions are available in the _Dataset_/_Evaluate_ folder. 
 
### Fine-tuning Phi-1.5 model on Kotlin dataset

The code for fine-tuning the model is located in the _Code_/_Finetune_ folder. The dataset used for fine-tuning is available in the _Dataset/Finetune
/Kotlin/_ folder. I used [LoRA](https://huggingface.co/docs/diffusers/training/lora) technique to reduce the number of model's parameters because it was too heavy to train. Evaluation after fine-tuning is in the same fine-tuning code in the _Dataset/Finetune/Kotlin/_ folder.

### Results

The results are as follows:

Dataset | Before fine-tuning | After fine-tuning on Kotlin

--- | --- | --- | --- | ---
--- | Edit sim | EM | Edit sim | EM 
Kotlin | 14.69 | 43.0 | 16.05 | 10.0
CodeXGLUE | 28.42 | 9.0 | 8.16 | 3.0
