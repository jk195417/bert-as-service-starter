# bert-as-service-starter

This starter include a Pipfile to install tensorflow + bert-serving-server.

- tensorflow 1.12.0 (using gpu support version as default), read: https://www.tensorflow.org/install
- bert-serving-server http, from https://github.com/hanxiao/bert-as-service
- bert model [`BERT-Base, Multilingual Cased`](https://storage.googleapis.com/bert_models/2018_11_23/multi_cased_L-12_H-768_A-12.zip), from: https://github.com/google-research/bert

## Requirments

- Git
- Python3
- pipenv

### GPU supprt Requirments

- Nvidia GPU
- CUDA 9.0
- CUDNN 7.4.2

## Setup

Clone this starter

```sh
$ git clone https://github.com/jk195417/bert-as-service-starter.git
$ cd bert-as-service-starter
```

Install dependencies

```sh
$ pipenv update
```

Download and unzip [`BERT-Base, Multilingual Cased`](https://storage.googleapis.com/bert_models/2018_11_23/multi_cased_L-12_H-768_A-12.zip) into `/models` dir

### None GPU support

If you don't want GPU support:

```sh
$ pipenv uninstall tensorflow-gpu
$ pipenv install tensorflow
```

## Usage

1 worker need 1G RAM, example: GTX 1060 6G can open 4 workers max.

```sh
# Start server at localhost:8125
$ pipenv run bert-serving-start -model_dir=./models/multi_cased_L-12_H-768_A-12 -num_worker=4 -http_port=8125 -http_max_connect=20
```

Press `ctrl+c` twice to shutdown server, then you can clean up those tmp dirs.
