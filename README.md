# transfer_learning_tensorflow
A easy transfer learning program using tensorflow and tensornets  
用tensorflow和开源库[tensornets](https://github.com/taehoonlee/tensornets)实现迁移学习。  
### 程序主要针对百度点石竞赛商家招牌分类，也可迁移到其他任务。
## 功能简介：
- 支持35个模型
- 可设置随机图像增强
- 可选择finetune的变量数
- 可restore保存的ckpt接着训练
## 说明
- 更换模型只需替换`model.DenseNet201`为你想要transfer learn的model，具体支持的模型请移步[tensornets](https://github.com/taehoonlee/tensornets)  
- 请将数据文件放置于datasets文件夹下运行model/train.py即可开始训练
- 运行model/test.py进行预测
## 重要参数说明：
- status: 有两个选项`train`和`restore`，分别代表训练和恢复存储的模型继续训练
- num_train_vars: 倒数多少个finetune的trainable variables，目前暂时没有实现选择finetune的层数，只支持变量数
- num_train_vars_before: 在`restore`模式下，可以结合 num_train_vars来进一步调整finetune的variable数量，比如一次训练微调了190个variables，现在想微调200个variables，那么将程序终止，设置`num_train_vars_before=190, num_train_vars=200`,再以`restore`模式训练即可
## requirements
- tensorflow
- tensornets
- pandas
## tensornets安装
- 请确保安装tensornets前已装好tensorflow
- Linux系统直接`pip install tensornets`或者`pip install git+https://github.com/taehoonlee/tensornets.git`即可
- Windows系统如果`pip install tensornets`失败，请先将tensornets的所有文件git到本地，打开setup.py，将其中的`libraries=['m'],`这句注释掉，然后执行`python setup.py install`即可
