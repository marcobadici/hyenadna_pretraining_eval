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

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system





## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
