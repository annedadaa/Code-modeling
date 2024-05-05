# Improving LLMs on underrepresented programming languages: Phi-1.5 model fine-tuned on Kotlin 

All the code was written in Python notebooks so there's no specific instruction on how to use them. The code is commented and it's more self-explained, here I introduce the main information.

### Dataset

Kotlin code dataset was collected from the [kotlinx.coroutines](https://github.com/Kotlin/kotlinx.coroutines.git) repository. The code for collecting the dataset is located in the _Code_ folder in the _Dataset_preprocessing_ subfolder. In total, 1049 Kotlin files were collected, and 100 of them were used to evaluate the model.

Python test set of the CodeXGLUE dataset was taken from the [CodeXGLUE repository](https://github.com/microsoft/CodeXGLUE/blob/main/Code-Code/CodeCompletion-line/dataset/py150/line_completion/test.json) and was used to evaluate the model. For comparability with the Kotlin test set, I took 100 samples of Python code, and each last line was taken as the target line that needs to be predicted. The code for Python data preprocessing is also available in the _Dataset_preprocessing_ subfolder of the _Code_ folder.

### Evaluation

The code used for evaluation is located in the _Code_/_Evaluate_ folder. I used [Phi-1.5 model](https://huggingface.co/microsoft/phi-1_5) to predict the next code lines for both Python and Kotlin datasets. Files with predictions are available in the _Dataset_/_Evaluate_ folder. 
 
### Fine-tuning Phi-1.5 model on Kotlin dataset

The code for fine-tuning the model is located in the _Code_/_Finetune_ folder. 

### Results

Describe the metrics and make some conclusion
