# turboSearch规划

## 思路

1. 将输入的句子进行分词
    1. 将输入的句子分词，作为每个元词
    2. 每个元词的内容包括：词的内容，词所在的位置，文档的id，词在文档出现的频率
2. 将所有的元词加入索引
    1. 每个关键词都对应着DocId，以及频率和位置
3. 将搜索的句子分词
    1. 词的内容包括：词的内容及词的位置和频率
4. 将搜索的分词进行索引搜索，得到的DocId进行评率及位置计算，进行Docid排序


## 基本实现
* [x] 对输入的内容加入分词队列，按句子进行分词处理，分词包括词的内容，词所在的位置，文档的id，词在文档出现的频率。
* [x] 去掉分词中常用词及标点符号。
* [x] 将文档分词加入索引。
* [x] 根据搜索种分词对索引内容进行查找，得到list。
* [x] 制定排序用的得分规则，计算每条符合结果的Doc得分情况。(得分方式需要修改)
* [ ] 输出。

## 进阶
* [ ] 制定规则，测试搜索效率。
* [ ] 研究go并发对搜索效率的影响。
* [ ] 研究如何分词处理，了解hash等数据结构对于快速查找的优势。
* [ ] 对索引加入树结构，加快查找速度。


# 待商讨问题
## 得分初步处理
获取同一个docid距离最短的情况，并除以次出现的频率和权值。
`score=min(dictance)*F*H\1`