# 前言
商品识别是零售结算的关键部分，本仓库采用基于PP-ShiTu的“**主体检测**、**特征提取**、**向量检索**”构成的图像识别技术。其中，特征提取部分对模型的识别结果至关重要。本仓库存储着ColugoMum项目团队长时间以来的实验成果，基于[RP2K](https://git.openi.org.cn/ColugoMum/Exprements-public/datasets)数据集进行的一些重要实验，可供开发者基于这些实验结论和模型进行模型的优化。并且，本仓库也提供针对不同场景的高精度推理模型，开发者可直接下载推理模型进行业务开发。

零售场景对于精度和速度有着极高的要求，其要求模型在确保精度的同时又要保证预测速度。因此，本仓库的模型选择会严格选取业内在**速度与精度**的平衡上有较好效果的模型。相关模型的介绍可以参照本仓库百科，详细介绍请参考其论文。

# RP2K数据集介绍
RP2K数据集收录了50万+张零售商品货架图片，商品种类超过2,000种，是目前零售类数据集中产品种类数量最多的数据集。不同于一般聚焦新产品的数据集，RP2K收录了超过50万张零售商品货架图片，商品种类超过2000种，该数据集是目前零售类数据集中产品种类数量TOP1，同时所有图片均来自于真实场景下的人工采集，针对每种商品，品览提供了十分详细的标注。RP2K致力于帮助物品识别领域进行学术研究，同时为AI物品识别从业者打造真实行业级试炼场。

## 商品识别的难点
在真实场景中，准确识别货架上零售产品仍然具有很高的挑战性。

1. 同一生产线中的产品可能具有不同的尺寸，并且它们通常外观高度相似但价格不同。图像尺寸无法反映产品的实际尺寸。
2. 制造商通常会为一条产品线制造多种口味，但是它们的外观在标签上只有非常细微的差别。
3. 执行人员在拍摄货架图片时，由于相机角度、拍摄环境不同，图片会产生变形，图像也可能被拉伸，甚至会出现曝光不足的现象。 从下面的样例图可以看到，RP2K针对以上可能的情况均有涉及，采用细粒度识别对商品进行甄别。

## RP2K数据集亮点
1. 就产品类别而言，毫无疑问，它是迄今为止全球规模最大的零售数据集，超过2000种SKU。
2. 所有图像均在自然采光的实体零售店中手动采集，与实际应用场景匹配度极高，具有极佳的实践落地适应性。
3. 品览为每种商品提供了丰富的注释，包括大小、形状和味道/气味。期待RP2K数据集可以为计算机视觉领域研究和零售行业AI落地赋能。

# 实验结果

## 消融实验
 |  model  | num epoch |  batch size/gpu cards |embedding size  | learning rate  |  cutout  |  RandomErasing  |  测试分辨率  |  top1 recall  | 配置文件 |
 | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
  | PP_LCNet_x2_5 | 100 | 256/1 |  512  |  0.02 |  N  |  N  |  224  | [96.40%](./model/Pre-trained_Model/PPLCNET_x_2_5/PPLCNet_x_2_5-base-log.txt) | [配置文件]() |
   | PP_LCNet_x2_5 | 100 | 256/1 |  512  |  0.02 |  N  |  N  |  288  | [96.76%](./model/Pre-trained_Model/PPLCNET_x_2_5/288-log.txt) | [配置文件]() |
 | PP_LCNet_x2_5 | 100 | 256/1 |  512  |  0.02 |  Y  |  N  |  288  | [96.90%](./model/Pre-trained_Model/PPLCNET_x_2_5/PPLCNET_x_2_5-512-log.txt) | [配置文件](https://git.openi.org.cn/ColugoMum/Exprements-public/src/branch/main/PaddleClas/ppcls/configs/Exprements/PPLCNet_x_2_5/PPLCNet_x_2_5-512-0.02-256-cutout.yaml) |
 | PP_LCNet_x2_5 | 100 | 256/1 |  4096  |  0.02 |  N  |  N  |  288  | [96.79%]() | [配置文件](./PaddleClas/ppcls/configs/Exprements/PPLCNet_x_2_5/PPLCNet_x_2_5-4096-0.02-256.yaml) |
 | PP_LCNet_x2_5 | 100 | 256/1 |  4096  |  0.02 |  N  |  Y  |  288  | [96.87%](./model/Pre-trained_Model/PPLCNET_x_2_5/RandomErasing-log.txt) | [配置文件](./PaddleClas/ppcls/configs/Exprements/PPLCNet_x_2_5/PPLCNet_x_2_5-4096-0.02-256-RandomErasing.yaml) | 
 | PP_LCNet_x2_5 | 100 | 256/1 |  4096  |  0.02 |  Y  |  N  |  288  | [96.91%](./model/Pre-trained_Model/PPLCNET_x_2_5/PPLCNET_x_2_5-4096-log.txt) | [配置文件](./PaddleClas/ppcls/configs/Exprements/PPLCNet_x_2_5/PPLCNet_x_2_5-4096-0.02-256-cutout.yaml) |

## best_model
 |  model  | num epoch |  batch size/gpu cards |embedding size  |  learning rate  |  top1 recall  | 配置文件 | 预训练模型 | 推理模型 |
 | :----: | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
  | PP_LCNet_x2_5 | 100 | 256/1 |  512  |  0.02 | [96.90%](./model/Pre-trained_Model/PPLCNET_x_2_5/PPLCNET_x_2_5-512-log.txt) | [配置文件](./model/Pre-trained_Model/PPLCNET_x_2_5/PPLCNET_x_2_5-512-log.txt) | [预训练模型](https://git.openi.org.cn/ColugoMum/Exprements-public.git/info/lfs/objects/eb83176fa119f9a82cabc142f1ff64b3a474649ea03da627f1b985afb3a43e8f/UFBMQ05FVF94XzJfNS01MTIucGRwYXJhbXM) | [推理模型](https://git.openi.org.cn/ColugoMum/Exprements-public/src/branch/main/model/Inference_Model/PPLCNET_x_2_5-512.tar.gz) |
 | PP_LCNet_x2_5 | 100 | 256/1 |  4096  | 0.02 | [96.91%](./model/Pre-trained_Model/PPLCNET_x_2_5/PPLCNET_x_2_5-log.txt) | [配置文件](./PaddleClas/ppcls/configs/GeneralRecognition/PPLCNet_x2_5.yaml) | [预训练模型](https://git.openi.org.cn/ColugoMum/Exprements-public.git/info/lfs/objects/a321114d58933caa84479e259aff3a49105cde2e006b729f3404f93671cd4632/UFBMQ05FVF94XzJfNS5wZHBhcmFtcw) | [推理模型](https://git.openi.org.cn/ColugoMum/Exprements-public/src/branch/main/model/Inference_Model/PPLCNET_x_2_5-4096.tar.gz) |
 | PP_LCNetV2_base | 120 | 256/1 |  4096   | 0.02 | [96.85%](./model/Pre-trained_Model/PPLCNETV2_base/PPLCNETV2_base-log.txt) | [配置文件]() | [预训练模型](https://git.openi.org.cn/ColugoMum/Exprements-public.git/info/lfs/objects/fda75806c471bec38012eed4f2206b0eda409ff442edcd15001ae0193a5c3c2a/UFBMQ05FVFYyX2Jhc2UucGRwYXJhbXM) | 推理模型 |
 | PPHGNet_tiny | 120 | 256/1 |  4096   | 0.02 | [96.87%](./main/model/Pre-trained_Model/PPHGNET_tiny/PPHGNET_tiny-log.txt) | [配置文件]() | [预训练模型](https://git.openi.org.cn/ColugoMum/Exprements-public.git/info/lfs/objects/64bf9a3500a42e3dc5e08570b3d64d2f10cb5b2f09b28c65a04c7e044182241b/UFBIR05FVF90aW55LnBkcGFyYW1z) | 推理模型 |
 | PPHGNet_small | 120 | 256/1 |  4096   | 0.02 | [96.87%](./model/Pre-trained_Model/PPHGNET_small/PPHGNET_small-log.txt) | [配置文件]() | [预训练模型](https://git.openi.org.cn/ColugoMum/Exprements-public.git/info/lfs/objects/977839304d664a9820c68ac8be2552360b9a32412f94df87607038e0048cc659/UFBIR05FVF9zbWFsbC5wZHBhcmFtcw) | 推理模型 |
 | PPHGNet_base | 120 | 256/1 |  4096   | 0.02 | [96.88%]() | [配置文件]() | [预训练模型]() | 推理模型 |

**注**：
1. 目前仍处于实验建设当中，并不能保证结果最优;
2. 目前本实验repo均基于飞桨PaddleClas提供；
3. 所有模型训练均基于OpenI所提供的A100服务器(GPU数：1，CPU数：8，内存(MB)：65536，共享内存(MB)：32768)。

# 招募
欢迎开发者们加入本仓库的[共建](https://git.openi.org.cn/ColugoMum/Exprements-public/issues/1)！ColugoMum渴望和开发者们一道，推动我国AI+零售行业新变革！

# 鸣谢
1. 感谢[基于MindSpore AI框架实现零售商品识别](https://github.com/pprp/GoodsRecognition.MindSpore)提供相关trick；
2. 感谢[PaddleClas](https://github.com/PaddlePaddle/PaddleClas)提供相关模型及技术支持。

# 引用
```
@misc{cui2021pplcnet,
      title={PP-LCNet: A Lightweight CPU Convolutional Neural Network}, 
      author={Cheng Cui and Tingquan Gao and Shengyu Wei and Yuning Du and Ruoyu Guo and Shuilong Dong and Bin Lu and Ying Zhou and Xueying Lv and Qiwen Liu and Xiaoguang Hu and Dianhai Yu and Yanjun Ma},
      year={2021},
      eprint={2109.15099},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```
