# 1.依赖 
python == 3.8.0

allennlp == 2.4.0

pip install allennlp -i https://pypi.tuna.tsinghua.edu.cn/simple

# 2.训练
## 2.1 使用脚本训练
### train
```buildoutcfg
python train.py
```
### eval
```buildoutcfg
python evaluate.py
```
### predict
```buildoutcfg
python predict.py
```
## 2.2 使用 allennlp train 训练 embedding+bag_of_embedding

### train
```buildoutcfg
allennlp train scripts/my_text_classifier.jsonnet --serialization-dir checkpoint --include-package my_text_classifier
```
### eval
```buildoutcfg
allennlp evaluate checkpoint/model.tar.gz data/movie_review/test.tsv --include-package my_text_classifier
```

### predict
```buildoutcfg
allennlp predict checkpoint/model.tar.gz data/movie_review/test.jsonl --include-package my_text_classifier --predictor sentence_classifier
```

## 2.3 使用 allennlp train 训练 bert embedding+bert pool
这里需要下载[bert预训练模型](https://huggingface.co/bert-base-uncased/tree/main)放到``bert_pretrain`文件夹下
### train
```buildoutcfg
allennlp train scripts/my_text_classifier_bert.jsonnet --serialization-dir checkpoint_bert --include-package my_text_classifier
```
### eval
```buildoutcfg
allennlp evaluate checkpoint_bert/model.tar.gz data/movie_review/test_small.tsv --include-package my_text_classifier
```

### predict
```buildoutcfg
allennlp predict checkpoint_bert/model.tar.gz data/movie_review/test.jsonl --include-package my_text_classifier --predictor sentence_classifier
```
