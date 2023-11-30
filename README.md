Image Classification for Humor-Judge-GPT
===========================
# 1 Environment building
- It is recommended to use Anaconda for environment management. The command to create an environment is as follows:
```bash
conda create -n torch python=3.6
```

- My testing environment is as follows:
```bash
torch==2.1.1
torchvision==0.16.1
scipy==1.7.3
numpy==1.19.4
matplotlib==3.5.1
cv2==4.8.1
tqdm==4.64.0
h5py==3.6.0
terminaltables==3.1.0
packaging==23.0
```
# 2 Creating dataset
## 2.1 Label file creation

- 本次演示以花卉数据集为例，目录结构如下：

```
├─flower_photos
│  ├─daisy
│  │      100080576_f52e8ee070_n.jpg
│  │      10140303196_b88d3d6cec.jpg
│  │      ...
│  ├─dandelion
│  │      10043234166_e6dd915111_n.jpg
│  │      10200780773_c6051a7d71_n.jpg
│  │      ...
│  ├─roses
│  │      10090824183_d02c613f10_m.jpg
│  │      102501987_3cdb8e5394_n.jpg
│  │      ...
│  ├─sunflowers
│  │      1008566138_6927679c8a.jpg
│  │      1022552002_2b93faf9e7_n.jpg
│  │      ...
│  └─tulips
│  │      100930342_92e8746431_n.jpg
│  │      10094729603_eeca3f2cb6.jpg
│  │      ...
```
- 在`Awesome-Backbones/datas/`中创建标签文件`annotations.txt`，按行将`类别名 索引`写入文件；
```
daisy 0
dandelion 1
roses 2
sunflowers 3
tulips 4
```
## 2.2 Data set segmentation
- Open `Humor-Judge-GPT/tools/split_data.py`
- Modify the `original dataset path` and the `divided save path.` It is strongly recommended that the divided save path `datasets` be left unchanged. The next step is based on the folder by default for operations
```
init_dataset = 'Your dataset path'
new_dataset = 'A:/Humor-Judge-GPT/datasets'
```
- 在`Awesome-Backbones/`下打开终端输入命令：
```
python tools/split_data.py
```
- 得到划分后的数据集格式如下：
```
├─...
├─datasets
│  ├─test
│  │  ├─humor
│  │  ├─inhumor
│  └─train
│     ├─humor
│     ├─inhumor
├─...
```
## 2.3 Making Dataset
- Ensure that the partitioned dataset is under `Humor-Judge-GPT/datasets.` If not, then change the dataset path under `get_annotation.py`;
```
datasets_path   = 'Your dataset path'
```
- Open a terminal under `Humor-Judge-GPT/` and enter the command:
```
python tools/get_annotation.py
```
- Get the generated dataset information files `train.txt` and `test.txt` under `Humor-Judge-GPT/datas`.


