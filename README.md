This repository is created based on [python-data-science-project](https://github.com/kaust-vislab/python-data-science-project).

1. Download the repository to *REPO*.

2. Navigate to *REPO*/docker. Create the docker image using the Dockerfile in this folder.

```bash
$ docker image build --file Dockerfile --tag caner_ids:2017 ../
```

3. Download the [CICIDS2017 dataset](http://205.174.165.80/CICDataset/CIC-IDS-2017/) to *DATASET*.

4. Run the container.

```bash
docker container run --user root --gpus all -it --rm --tty \
	--volume *REPO*/data:/home/csigb/app/data \
	--volume *REPO*/notebooks:/home/csigb/app/notebooks \
	--volume *REPO*/results:/home/csigb/app/results \
	--volume *DATASET*:/home/csigb/app/dataset \
	--publish 8888:8888 \
	caner_ids:2017
```

5. Run "prepare_data.ipynb" to preprocess the dataset files and create features.npy and labels.npy.

6. Run "train_models.ipynb" to train 18 DNNs. The models we trained are already stored in *REPO*/results/Models. They will be overwritten.

7. Run "test_models.ipynb" to test 18 DNNs. The success rates will be written into *REPO*/results/Accuracies.

8. Run "analyze_features.ipynb" for feature analysis experiments. The success rates will be written into *REPO*/results/Accuracies.

9. Run "plot_results.ipynb" to create the plots for the results. The plot images will be written into *REPO*/notebooks.
