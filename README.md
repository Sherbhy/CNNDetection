## Setup

### Install packages
- Install PyTorch ([pytorch.org](http://pytorch.org))
- `pip install -r requirements.txt`

### Download model weights
- Run `bash weights/download_weights.sh`


## Quick start

### Run on a single image

This command runs the model on a single image, and outputs the uncalibrated prediction.

```
# Model weights need to be downloaded.
python demo.py -f examples/real.png -m weights/blur_jpg_prob0.5.pth
python demo.py -f examples/fake.png -m weights/blur_jpg_prob0.5.pth
```

### Run on a dataset

This command computes AP and accuracy on a dataset. See the [provided directory](examples/realfakedir) for an example. Put your real/fake images into the appropriate subfolders to test.

```
python demo_dir.py -d examples/realfakedir -m weights/blur_jpg_prob0.5.pth --batch_size 1
```

## Evaluation

After the testset and the model weights are downloaded, one can evaluate the models by running:

```
# Run evaluation script. Model weights need to be downloaded. See eval_config.py for flags
python eval.py
```

Besides print-outs, the results will also be stored in a csv file in the `results` folder. Configurations such as the path of the dataset, model weight are in `eval_config.py`, and one can modify the evaluation by changing the configurations.
