## Installing

### Anaconda
Only Mac and Unix environments currently supported

1. ```conda env create -f cs182_{os}.yaml```, where os can be ``unix`` or ``mac``
2. ```pip install -e ./baselines```

### PIP

Only Mac and Unix environment currently supported
1. Create your virtual environment and activate it
2. ```pip install -r requirements_{os}.txt```, where os can be ```unix``` or ```mac```

## Training

To train a network, you must first create a configuration file and store it in the ``configurations/``
folder. Examples of configurations can be seen in ``ppo_baseline_cuda.yaml`` and ``ppo_imapala_cuda.yaml``.
Default values for any configuration can be seen ``defaults.py``.

Given a configuration ``configurations/example.yaml`` you can run training with the following command:

``python train_fruitbot.py --config configurations/example.yaml``

This will save run information to the folder ``runs/example/{current datetime}``. Run information includes
checkpoints and relevant environment/training information in a .csv format. The same information will be printed
in the terminal during training. See ``baselines.logger`` for more details.

## Testing

To test a network, you must supply two things:
1. Location of a pre-trained model i.e. ``runs/example/2020-05-05-10-07/checkpoints/best.ckpt``
2. Location of configuration file used to train aforementioned model i.e. ``configurations/example.yaml``

The command to test looks like:

``python test_fruitbot.py --config configurations/example.yaml --model_path runs/example/2020-05-05-10-07/checkpoints/best.ckpt``

See ``defaults.py`` to see testing configuration defaults; of note are the NUM_LEVELS and LEVEL_SEED configurations -- these along with the model choice uniquely specify a testing instance. We recommend testing across all models with the same LEVEL_SEED to give comparable results.

Results for the above command would be stored in ``runs/example_test/2020-05-05-10-07/``
