# Seminar Praktikum - Evaluation of the effect of pre-training on HyenaDNA models of varying sizes on genomic sequence classification tasks  

This project investigates the impact of pre-training on the performance of HyenaDNA models in genomic sequence classification tasks, comparing
fine-tuning pre-trained models with training from scratch. Utilizing datasets from GenomicBenchmarks, the study evaluates both small (1k tokens) 
and large (1 million tokens) model configurations to determine if pre-training benefits scale with model size. The results provide insights into
optimizing computational resources and training protocols, suggesting that pre-training may not always be necessary and could be enhanced by using 
different genomic datasets or longer sequence tasks. The project includes detailed methodologies, performance metrics, and analysis outcomes to 
guide future genomic model development.


## Getting Started

These instructions will allow you to understand what the scripts do, how they were run, and how the outputs were then processed.

### Prerequisites

The experiments petaining to this study were conducted utilizing the Google Colab notebook provided by the authors of the original paper, available
at https://colab.research.google.com/drive/1wyVEQd4R3HYLTUOXEEQmp_I8aNC_aLhL?usp=sharing. The notebook contains the necessary components for initializing
the Hyena Operator, retrieving the data for training and testing, setting up the character tokenizer, and finally putting the necessary pieces together.
If attempting to replicate the experiments, the provided notebooks in this repo are currently in the 1M configuration as this was the last set of experiments
that was run. In order to do this, the A100 GPU is necessary, thus requiring Colab Pro+. Running the model in the 1K configuration allows for the use of the
T4 GPU, which comes with the free membership.

### Installing

The authors in their github repo, available here: https://github.com/HazyResearch/hyena-dna, provide the necessary elements for setting up an environment
with the necessary installs and then running their code locally. The problem for us was computational in nature, thus we relied on the Colab implemenation
instead to have access to cloud compute. Thus, this made the setup more simple, all the installs being included and are sure to be compatible with Google's
cloud service.


## Running the tests

The necessary scripts are contained within the 'scripts' folder in the main branch. They are the following: 'HyenaDNA_training_&_inference__large_1M.ipynb' is
a modification of the original script mentioned above. It is mainly the original code, containing the modifications mentioned by the authors, namely cosine decay
learning rate scheduler, gradient clipping at 1.0, and optimizer parameter groups for setting layer-specific hyperparameters. It is currently setup for the 
1M model. Secondly, there is the 'HyenaDNA_training_scratch.ipynb' script, which is setup for training the model from scratch. As opposed to the previous script,
here we utilize the original notebook up to the point of importing the configuration and weights for the model we are investigating, in this case also the 1M 
model as this was the last one investigated, after which we initialize the weights from scratch and only make use of the configuration. The following elements 
are similar to the first script, with the character tokenizer, train and test functions, dataset retrieval, and parameter setup.

To show further the way I worked with these notebooks, firstly I will address the model size. In both scripts mentioned previously, the model name, being either
'hyenadna-large-1m-seqlen' or 'hyenadna-tiny-1k-seqlen', appears frequently at multiple locations. Whenever working with a specific model, I would manually go through
the code and make changes at the necessary locations, either in the run_train function for the pre-trained model in order to make sure the right architecture and 
configuration is downloaded, on in the case of the model trained from scratch the model name is mentioned at multiple points, such as for the loading of the
pre-trained weights or for the initialization from scratch. As of now, both scripts are configured for the 1M model and can be run as is. Second manual modifications
revolves around the name of the dataset within the run_train function. This would be replaced with the necessary dataset name before each
run.

The scripts are setup such that the naming of the files is done automatically, with the type of file (confusion matrix, model weights, accuracies for train and test), 
number of epochs, name of dataset, and in the case of scratch models the seed utilized being included in the title. Because of the use of Colab, the filed had to then
be manually downloaded. Folders were created for each downstream task, and all the files generated from every run pertaining to that specific task were gathered together.

The last script, 'generation_outputs' was utilized for the analysis of the downloaded outputs. The files in which the outputs were saved had the following structure: 'all_'
followed by a short identifier. The script finds all these folders, then parses the outputs, being able to identify the necessary elements such as 1k or 1m for model size,
15 or 50 for number of epochs, the dataset, and seed. These are then stored for plotting. Plotting for the runs with 15 epochs are handled together, for the 1m and 1k models
with plots for the same dataset and model size being shown side by side, progress of training and testing accuracies. Plot for 50 epochs is similar but handled separately.
Finally, based on the generated confusion matrices I computed by hand multiple metrics for each task, such as accuracy, F1, recall, and precision. I ended up not including
these as they were beyond the scope of the research, and because I noticed some inconsistencies in the results, signifying that I made some mistakes when computing the 
values by hand. I have since double checked the accuracies which are correct and those are included in the final report. The final table contains the final test accuracy
from each task as to compare to the computed accuracy, and while slight differences exist, they are comparable.


## Acknowledgments

* Great thanks to my supervisor, Niklas Schmidinger, for his support and help!
* Further thanks to the authors who have provided great resources for the implementation and running of the experiments!
