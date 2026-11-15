# 2026-11-11_谢庚辰_ISBI_Contrastive‑Graph‑Cross‑View‑PD
汇报人：谢庚辰
Title：Graph-Guided Contrastive Alignment for SPECT and Clinical DaTQUANT Multimodal Parkinson’s Diagnosis
发表情况：ISBI 2024
收录情况：ISBI 2024 Open Access
作者：Jun‑En Ding, Chien‑Chin Hsu, Feng Liu
机构：Stevens Institute of Technology, Kaohsiung Chang Gung Memorial Hospital

## 摘要
帕金森病（PD）诊断中，SPECT影像与DaTQUANT结构化临床指标是两类重要异构模态。现有多模态融合方案容易出现模态霸权，高信息容量的图像分支主导训练、临床分支发生“躺平”，模态表征空间相似逻辑脱节，融合增益有限。为解决该问题，本文提出一种图引导的对比对齐多模态融合框架用于PD/HC二分类。该框架两条并行分支：图像分支使用ResNet18提取SPECT切片特征，临床分支直接输入12维DaTQUANT指标；基于病人样本之间KNN邻接关系构建患者图，利用GAT做图注意力编码，学习患者之间的邻接伪标签作为弱监督信号。模型借助跨模态对比损失对齐图像、临床两个独立表征空间，约束模态之间的相似性逻辑保持一致；同时搭配双分支独立分类损失与对角正则项共同优化，一次计算相似度矩阵S，复用在对比损失正负样本、双分支分类头约束、对角正则三处。实验表明，该方法可以有效缓解模态霸权，让临床分支学到有效疾病特征，在SPECT+DaTQUANT帕金森识别任务上，相比直接拼接、逐元素相加等基础融合方式取得更好的敏感度、特异度，同时降低模型预测方差。整体上，该工作证明利用患者样本关系图做弱监督对比对齐，是提升异构医学多模态融合可靠性的有效思路。

## 链接
发表情况：ISBI 2024，2024.5.27–30，Athens, Greece
收录情况：IEEE Xplore / PubMed / PMC（PMID: 39398281）
论文：https://ieeexplore.ieee.org/document/10635712
PubMed：https://pubmed.ncbi.nlm.nih.gov/39398281/
arXiv：https://arxiv.org/abs/2311.14902
数据集：Kaohsiung Chang Gung Memorial Hospital 内部 412 例 Tc‑99m‑TRODAT SPECT

## 讨论记录
1 可以学习该框架的双分支独立表征+图引导对比对齐架构，图像、结构化临床分支各自编码，不直接早期融合，用对比损失做空间对齐而不是设计复杂融合算子。
2 可以借鉴“患者KNN图+伪邻居标签”的弱监督思路：把样本之间的疾病相似关系作为额外监督信号，弥补标签稀少、模态异构带来的训练失衡问题。
3 可以借鉴相似度矩阵S复用的设计，一份相似度矩阵同时服务对比损失、分类约束、正则项，减少冗余计算，统一模态之间的相似逻辑。
4 对我的研究启发：后续可以扩展到帕金森更多异构模态（手写、步态、语音、MRI/DTI），把不同模态表征放到统一对比空间对齐；也可以把该对齐思路和因果干预、多模态大模型结合，进一步弱化模态霸权，提升泛化能力。