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
