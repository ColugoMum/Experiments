# Exprements
目前主要针对[零售行业商品特征学习数据集](https://aistudio.baidu.com/aistudio/datasetdetail/108651)及[RP2K](https://www.pinlandata.com/rp2k_dataset)两个数据集进行相关实验，主要存储一些商品识别的实验结果及日志。
## 针对[零售行业商品特征学习数据集](https://aistudio.baidu.com/aistudio/datasetdetail/108651)进行相关实验：
 |  model  | num epoch |  batch size/gpu cards |  learning rate  |  use cutout  |  use ssld  |  top1 recall  | 配置文件 |
 | :----: | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
 | PP_LCNet_x2_5 | 400 | 256/4 | 0.01 | N | N | [98.189%](./exprements/log/98189.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_01.yaml) |
 | PP_LCNet_x2_5 | 400 | 256/4 | 0.01 | Y | N | [98.21%](./exprements/log/98216.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_01_cutout.yaml) |
 | PP_LCNet_x2_5 | 400 | 256/4| 0.005 | N | N | [98.201%](./exprements/log/98201.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_005.yaml) |
 | PP_LCNet_x2_5 | 400 | 256/4| 0.005 | Y | N | [98.29%](./exprements/log/98291.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_005_cutout.yaml) |
 | PP_LCNet_x2_5 | 400 | 256/4 | 0.001 | Y | N | 98.26% |配置文件|
 | PP_LCNet_x2_5 | 400 | 64/4 | 0.005 | Y | Y | 98.30% | 配置文件|
 | PP_LCNet_x2_5 | 400 | 64/4 | 0.0025 | Y | Y | [98.37%](./exprements/log/98379.log) | 配置文件 |
 | PP_LCNet_x2_5 | 400 | 64/4 | 0.002 | N | Y | [98.38%](./exprements/log/98383.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_dml_002.yaml) |
 | PP_LCNet_x2_5 | 400 | 64/4 | 0.002 | Y | Y | [98.39%]((./exprements/log/98395.log)) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_dml_002_cutout.yaml) |
 | PP_LCNet_x2_5 | 400 | 128/4 | 0.004 | N | Y | [98.44%](./exprements/log/98442.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_004.yaml) |
 | PP_LCNet_x2_5 | 400 | 128/4 | 0.004 | Y | Y | [98.38%](./exprements/log/98376.log) | [配置文件](./exprements/PaddleClas/ppcls/configs/GeneralRecognition/GeneralRecognition_PPLCNet_x2_5_004_cutout.yaml) |

## 针对[RP2K](https://www.pinlandata.com/rp2k_dataset)进行相关实验

### RP2K数据集介绍
RP2K数据集收录了50万+张零售商品货架图片，商品种类超过2,000种，是目前零售类数据集中产品种类数量最多的数据集。不同于一般聚焦新产品的数据集，RP2K收录了超过50万张零售商品货架图片，商品种类超过2000种，该数据集是目前零售类数据集中产品种类数量TOP1，同时所有图片均来自于真实场景下的人工采集，针对每种商品，品览提供了十分详细的标注。RP2K致力于帮助物品识别领域进行学术研究，同时为AI物品识别从业者打造真实行业级试炼场。

#### 商品识别的难点
在真实场景中，准确识别货架上零售产品仍然具有很高的挑战性。

1. 同一生产线中的产品可能具有不同的尺寸，并且它们通常外观高度相似但价格不同。图像尺寸无法反映产品的实际尺寸。
2. 制造商通常会为一条产品线制造多种口味，但是它们的外观在标签上只有非常细微的差别。
3. 执行人员在拍摄货架图片时，由于相机角度、拍摄环境不同，图片会产生变形，图像也可能被拉伸，甚至会出现曝光不足的现象。 从下面的样例图可以看到，RP2K针对以上可能的情况均有涉及，采用细粒度识别对商品进行甄别。
#### RP2K数据集亮点
1. 就产品类别而言，毫无疑问，它是迄今为止全球规模最大的零售数据集，超过2000种SKU。
2. 所有图像均在自然采光的实体零售店中手动采集，与实际应用场景匹配度极高，具有极佳的实践落地适应性。
3. 每种商品提供了丰富的注释，包括大小、形状和味道/气味。期待RP2K数据集可以为计算机视觉领域研究和零售行业AI落地赋能。
### 相关实验结果
 |  model  | num epoch |  batch size/gpu cards |  learning rate  |  top1 recall  |  预训练模型  |
 | :----: | :---- | :---- | :---- | :---- | :---- |
 | PP_LCNet_x2_5 | 100 | 256/1 | 0.01 | [96.10%](./best_model/RP2K/Zhaoyian/train_zhaoyian.log) |  [预训练模型](./best_model/RP2K/Zhaoyian/best_model.pdparams) |
 | PP_LCNetV2 | 100 | 256/1 | 0.01 | [96.65%](./best_model/RP2K/PPLCNETV2/train.log) | [预训练模型](./best_model/RP2K/PPLCNETV2/train_model/best_model.pdparams) |
