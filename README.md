# NLP-BERT-EmotionClassification

## 数据集介绍

Sentiment Analysis (stanford.edu)  Large Movie Review Dataset是一个二元情绪分类的数据集，训练集和测试集分别包含25000条电影评论，还有额外50000条未标记数据。
该数据集由电影评论和情感极性标签组成，标签满分为10分，若标签小于4代码这是一条负面评论，若标签大于7代表这是一条正面评论。该数据集的带标签数据中正面评论和负面评论分别有25000条。
除此之外，每个电影的评论不超过30条，因为多了可能会存在相关性。

## 模型对比

### BERT模型

Bert 是 2018 年由 Google 推出了，整体是一个自编码语言模型（Autoencoder LM）,即一个预训练的语言表征模型。
在BERT之前采用预训练+微调模式的模型有ELMo和GPT，BERT在ELMo的基础上采用transformer模块代替了之前的LSTM模块，GPT和BERT的最大的不同是：GPT里的基本结构是由单向的Transformer-Decoder结构组成，而BERT是由双向的Transformer-Encoder结构组成。
它强调了不再像以往一样采用传统的单向语言模型或者把两个单向语言模型进行浅层拼接的方法进行预训练，而是采用新的 masked language model（MLM），以致能生成深度的双向语言表征。BERT使用两种预训练策略：MLM和NSP。BERT 论文发表时提及在11个NLP任务中获得了新的 sota的结果。基本原理如下图所示：
 
BERT 模型通常有两种规模:BERT-Base 有 12 层 Transformer 编码器,BERT-Large 有 24 层。

### RoBERTa

RoBERTa在2019年由Facebook AI Research提出，是BERT更为精细的调优版本。Bert在MLM训练中，提早把要mask的token处理好，在训练时训了多个epoch。这样在不同的epoch中，同一条sample总是使用相同的mask进行训练。Roberta使用了dynamic mask，即每条数据在训练前才随机决定进行mask的位置，这样不同的epoch之间同一条样本也有不同的mask结果，提升了数据多样性。Bert使用了MLM和NSP两个任务，而Roberta通过实验发现NSP的作用不大，因此直接取消了NSP任务。Roberta增大了batch size，提高训练效率，以获取更好的训练结果。Roberta增大了训练数据和训练step数，实验表明模型继续训练还能进一步收敛。Bert使用WordPiece分词，而Roberta使用BBPE，增大了词表。

### DeBERTa

DeBERTa于2020年由微软亚洲研究院和中国科学技术大学联合研究开发，是另一款基于BERT的变体模型。DeBERTa通过引入注意力机制中的解耦注意力和解码增强技术，解决了BERT在注意力机制中的问题。DeBERTa在训练过程中引入了自注意力机制的变体，以减少注意力分数的偏差。此外，DeBERTa还通过解码增强技术提高了模型的泛化能力。
