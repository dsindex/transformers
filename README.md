# Description

reference code for [transformers](https://github.com/huggingface/transformers) of huggingface

# Requirements

```
* python 3.6
* CUDA 10
$ pip install tensorflow-gpu==2.0
$ pip install torch==1.2.0
$ pip install git+https://github.com/huggingface/transformers.git
$ pip install seqeval
$ pip install tensorboardX
```

# Examples

- BERT usage
```
$ python example1.py
```

# NER for CoNLL2003 eng dataset(using word only)

- train and evaluate
```
$ ./train-ner.sh -v -v

* select the checkpoint dir for the best model, you may refer to the tensorboard.
* modify evalt-ner.sh
* ex) evaluate ${OUTPUT_DIR}/checkpoint-3550
$ ./eval-ner.sh -v -v

1. bert-base-cased

* dev.txt

* test.txt

2. bert-large-cased

* dev.txt

* test.txt

3. roberta-large

* find possible max-f1-score using 'test.txt' with evaluate_during_training
  => results, _ = evaluate(args, model, tokenizer, labels, pad_token_label_id, mode="test")

* dev.txt
f1 = 0.9560697518443997
loss = 0.047375404791811564
precision = 0.9525559639158035
recall = 0.9596095590710199

* test.txt
f1 = 0.9216322948661694
loss = 0.15627447860190471
precision = 0.913694101270228
recall = 0.9297096317280453

```

- tensorboardX
```
$ tensorboard --logdir engeval-model/runs/ --port port-number --bind_all
```

- f1 score for dev set
![](/data/eval_f1.png)
