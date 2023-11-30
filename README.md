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

- The directory structure of dataset is as follows:

```
├─dataset
│  ├─humor
│  │      .jpg
│  │      .jpg
│  │      ...
│  ├─inhumor
│  │      .jpg
│  │      .jpg
│  │      ...

```
- Create the tag file `annotations.txt` in `Humor-Judge-GPT/datas/` and write the `category name index` to the file by line;
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
- Open a terminal under `Humor-Judge-GPT/` and enter the command:
```
python tools/split_data.py
```
- The format of the partitioned dataset is obtained as follows:
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


