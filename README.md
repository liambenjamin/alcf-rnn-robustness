# alcf-rnn-robustness
Codes supporting RNN project at ALCF.

### File Contents

The model training script is located at ``src/train.py``. This script takes training arguments located in the ``hyperparameter-configurations`` directory. Each argument configuration is named ``hypers.<id>``, and contains a dictionary of arguments that is parsed and fed to the training script with ``sys.argv``. For example, ``hypers.0`` contains:

```
{
	"architecture": "rnn", 
	"learning_rate": 0.0001, 
	"dimension": 128, 
	"epochs": 25, 
	"dataset": "mnist", 
	"permute": true, 
	"pad": 0, 
	"orientation": null
}
```

Executing training with a specific hyperparameter configuration can be performed from the terminal with:

	$ python train.py hyperparameter-configurations/hypers.1  

### Accessing Data

The datasets used for training need to be downloaded once prior to running training scripts. Once the datasets are downloaded, internet connection is no longer needed. To download the datasets open a python session and run:

	> from tensorflow.keras.datasets import mnist, fashion_mnist
	> mnist.load_data()
	> fashion_mnist.load_data()
	> exit()

This will download the datasets to ``~/.keras/datasets`` and make them available for the training script to access at runtime. Executing the training script will load and augment the downloaded datasets according to the arguments stored in ``hypers.<id>``. 
