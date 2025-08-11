# longDoc
This repository includes papers and codes about Sparse Attention, Long-Term Memory and Evaluation for Long Context Modeling.

# Papers
|Method|Paper|Code| Description |Blog|
|-|-|-|-|-|
|MemAgent|[paper](https://arxiv.org/pdf/2507.02259)|[code](https://github.com/BytedTsinghua-SIA/MemAgent)||[知乎](https://zhuanlan.zhihu.com/p/1937241000385967147)|
|InfLLM v2|||改进了 相关性score的计算方法，将K根据seq维度分成多个更小的语义 kernel ，相当于更小的滑窗。用mean pooling 代表 语义kernal，是parameter-free的操作，可以通过优化 token 级别的key vector 来间接优化语义kernal的表示|[知乎](https://zhuanlan.zhihu.com/p/1936526523361375905)|
|Gemma3|||global only 为普通的full-attention模型，1：1 sw=4096为1个global attention后夹一个local attention（4096 窗口长度），从图中显示主要节约了kv cache部分的显存||
|Qwen2.5 1-M|||Dual Chunk Attention : 问题：过长的token在没有经过训练的position后效果变差，The DCA method addresses this issue by dividing the entire sequence into multiple chunks and remapping the relative positions into smaller numbers, 确保任意两个标记之间的距离不超过预训练长度 + 稀疏注意力||
|Native Sparse Attention|||||
|MoBA|||MOBA可以根据门控单元自主动态选择要关注哪些block，选择核心逻辑是用key的mean pooling 和query做matmul算出Block维度的相似度，选择TOP K个相似块|[知乎](https://zhuanlan.zhihu.com/p/29537550511)|
|Infinite-LLM|[paper](https://arxiv.org/pdf/2401.02669)||针对LLM服务的动态性，提出了一种高效的LLM服务系统Infinite-LLM。通过在集群级调度KVCache，它能够有效地支持可扩展的上下文长度，从而平衡实例之间的资源需求，实现高整体系统吞吐量||




# Benchmarks

|Name|paper|code|description|
|-|-|-|-|
|InfiniteBench||	[code](https://github.com/OpenBMB/InfiniteBench/blob/main/README_ZH.md)|InfiniteBench 测试数据的平均上下文长度为195k，InfiniteBench 评测集包含12个任务，包括中英双语，涵盖了检索、数学、代码、问答、和摘要等5个领域|
|LongCite|[paper](https://arxiv.org/abs/2409.02897)|[code](https://github.com/THUDM/LongCite/tree/main)|以句子粒度在每个句子前加索引[x],根据问题找到引用|
|FinLongEval||[code](https://github.com/valuesimplex/FinLongEval)|面向金融场景的长文档评测集，8 大类金融长文档和 12 大类问题，共计 43 篇金融长文档和 347 道问题|
|RULER|	[paper](https://arxiv.org/abs/2404.06654)|[code](https://github.com/NVIDIA/RULER)|综合性的评估benchmark，包含13个任务，4个分类（Retrieval，Question Answering，Multi-hop Tracing，Question Answering）|
