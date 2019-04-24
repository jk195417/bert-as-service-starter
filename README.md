# bert-as-service-starter

This starter include a Pipfile to install TensorFlow with GPU support + bert-as-service, and the `BERT-Base, Multilingual Cased` model.

- tensorflow-gpu, read: https://www.tensorflow.org/install/gpu
- bert-as-service http server, from https://github.com/hanxiao/bert-as-service
- bert model [`BERT-Base, Multilingual Cased`](https://storage.googleapis.com/bert_models/2018_11_23/multi_cased_L-12_H-768_A-12.zip), from: https://github.com/google-research/bert

## Requirments

- Git
- Python3
- pipenv
- GPU(hardware + driver + CUDA + CUDNN)

## Setup

Clone this starter

```sh
$ git clone https://github.com/jk195417/bert-as-service-starter.git
$ cd bert-as-service-starter
$ pipenv update
```
Download and unzip [`BERT-Base, Multilingual Cased`](https://storage.googleapis.com/bert_models/2018_11_23/multi_cased_L-12_H-768_A-12.zip) into `/models` dir

## Usage

1 worker need 1G RAM, example: GTX 1060 6G can open 4 workers max.

```sh
# Activate virtualenv
$ pipenv shell
# Start server at localhost:8125
$ pipenv run bert-serving-start -model_dir=./models/multi_cased_L-12_H-768_A-12 -num_worker=4 -http_port=8125 -http_max_connect=20
```

Press `ctrl+c` twice to shutdown server, then you can clean up those tmp dirs.
