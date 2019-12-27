# Albert-zh for pytorch-transformers
- 僅僅是基於**參考**進行轉換，然後踩踩雷
- Albert zh for [pytorch-transformers](https://github.com/huggingface/transformers)
- 測試支援繁體中文

## 可用模型 
- [albert_tiny_zh](https://github.com/p208p2002/albert-zh-for-pytorch-transformers/releases/download/am_v1.1/albert_tiny.zip)
- [albert_base_zh](https://github.com/p208p2002/albert-zh-for-pytorch-transformers/releases/download/am_v1.1/albert_base.zip)
- [albert_large_zh](https://github.com/p208p2002/albert-zh-for-pytorch-transformers/releases/download/am_v1.1/albert_large.zip)
- [albert_xlarge_zh](https://github.com/p208p2002/albert-zh-for-pytorch-transformers/releases/download/am_v1.1/albert_xlarge.zip)

## API
`from albert_zh import ...`
```
AlbertConfig
AlbertTokenizer
AlbertModel
AlbertForMaskedLM
AlbertForQuestionAnswering
AlbertForSequenceClassification
```
> https://huggingface.co/transformers/v2.3.0/model_doc/albert.html

## 使用方法
- 除 model class、model config 改由 albert_zh 引入外，其餘可續用transformers
> https://github.com/lonePatient/albert_pytorch/issues/35
- 測試在 transformers 2.3.0 正常運作
> 使用 albert-base 在[台達電閱讀理解資料集](https://github.com/DRCKnowledgeTeam/DRCD)得到f1 score: 82.0375
- 詳細用法參見`usage_example.py`

## 常見問題
#### AttributeError: 'BertConfig' object has no attribute 'share_type'
config.json增加`"share_type":"all"`

#### 訓練時模型亂印東西
請用`log()`代替`print()`，並且在程式開始的時候先執行一次`blockPrint()`
```python
import os,sys
def log(*logs):
    enablePrint()
    print(*logs)
    blockPrint()

# Disable
def blockPrint():
    sys.stdout = open(os.devnull, 'w')

# Restore
def enablePrint():
    sys.stdout = sys.__stdout__
```

## 測試環境
- python 3.6.4
- pyotrch 1.3 (with cuda 10)
- transformers 2.3.0

## 參考
### albert zh
- https://github.com/brightmart/albert_zh
### albert tf to pytorch
- https://github.com/lonePatient/albert_pytorch
