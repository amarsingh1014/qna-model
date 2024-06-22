# QnA Model

This repository contains the code to run the model built for the QnA dataset.

## Getting Started

To set up the project, follow these steps:

1. Run the following command to download the QnA dataset and GloVE Vectors:

   ```
   ./get_started.sh
   ```

   This script uses `requirements.txt` to install the necessary dependencies.

2. After running the script, you'll have:
   - A new directory called `data` with the train and dev json files for the QnA dataset.
   - An empty folder called `experiments` that will store the results of your experiments.

## Running the Models

To run the code, use `main.py` in the `code` directory.

### BIDAF Model

To run the BIDAF model, use the following command:

```
python code/main.py --experiment_name=bidaf_best --dropout=0.15 --batch_size=60 --hidden_size_encoder=150 --embedding_size=100 --do_char_embed=False --add_highway_layer=True --rnet_attention=False --bidaf_attention=True --answer_pointer_RNET=False --smart_span=True --hidden_size_modeling=150 --mode=train
```

### RNET Model

To run the RNET model, use the following command:

```
python code/main.py --experiment_name=rnet_best --dropout=0.20 --batch_size=20 --hidden_size_encoder=200 --embedding_size=300 --do_char_embed=False --add_highway_layer=False --rnet_attention=True --bidaf_attention=False --answer_pointer_RNET=True --smart_span=True --mode=official_eval --json_in_path=data/tiny-dev.json --json_out_path=predictions_rnet.json --ckpt_load_dir=experiments/rnet_best/best_checkpoint
```

## Results

After running the models, a new folder named `experiments` will be created, containing the results of your code runs.

## Visualizing Results with TensorBoard

To start TensorBoard and visualize your results, run the following commands:

```
cd experiments  # Go to experiments directory
tensorboard --logdir=. --port=5678  # Start TensorBoard
```

This will launch TensorBoard, allowing you to view and analyze the results of your experiments.
