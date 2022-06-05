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

## 针对[RP2K](https://www.pinlandata.com/rp2k_dataset)进行相关实验：
 |  model  | num epoch |  batch size/gpu cards |  learning rate  |  top1 recall  |  
 | :----: | :---- | :---- | :---- | :---- |
 | PP_LCNet_x2_5 | 100 | 256/1 | 0.01 | [96.10%](./best_model/RP2K/Zhaoyian/train_zhaoyian.log) |  
 | PP_LCNetV2 | 100 | 256/1 | 0.01 | [96.65%](./exprements/log/98216.log) |
