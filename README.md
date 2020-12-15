## Note
The refer.py file can load all 4 referring expression datasets, i.e., RefClef, RefCOCO, RefCOCO+ and RefCOCOg.They are with different train/val/test split by UNC, Google and UC Berkeley respectively. We provide all kinds of splits here. We used only RefCOCO, RefCOCO+, and RefCOCOg datasets for the experiments and analysis
<!--<table width="100%">
<tr>
<td><img src="http://bvisionweb1.cs.unc.edu/licheng/referit/refer_example.jpg", alt="Mountain View" width="95%"></td>
</tr>
</table>-->

## Citation
We used the following two datasets: RefCOCO and RefCOCO+, which were collected by UNC. So we are citing their EMNLP2014 paper; We also compared the results from previous state-of-art model with the visual comparison. Hence, we are citing ECCV2016 paper by Licheng et al..
```bash
Kazemzadeh, Sahar, et al. "ReferItGame: Referring to Objects in Photographs of Natural Scenes." EMNLP 2014.
Yu, Licheng, et al. "Modeling Context in Referring Expressions." ECCV 2016.
```

## Setup
Run "make" before using the code.
It will generate ``_mask.c`` and ``_mask.so`` in ``external/`` folder.
These mask-related codes are copied from mscoco [API](https://github.com/pdollar/coco).

## Download
Download the cleaned data and extract them into "data" folder.
- 1) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refclef.zip (optional)
- 2) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refcoco.zip
- 3) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refcoco+.zip 
- 4) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refcocog.zip 

## Preparing Images:
Since we colud not push the large volume of datasets to this repo, we provided the instructions for downloading the datasets and setting up the data directory. Also a directory tree has been provided into the data directory. Please refer to the readme.md file in the data directory.
```bash
cd "data/" directory.
mkdir images
cd images/
mkdir mscoco
wget http://images.cocodataset.org/zips/train2014.zip
```
COCO's images are used for RefCOCO, RefCOCO+ and refCOCOg.

## How to use
The "refer.py" is able to load all 4 datasets with different kinds of data split by UNC, Google, UMD and UC Berkeley.
**Note for RefCOCOg, we suggest use UMD's split which has train/val/test splits and there is no overlap of images between different split.**
```bash
# locate your own data_root, and choose the dataset_splitBy you want to use
refer = REFER(data_root, dataset='refclef',  splitBy='unc')
refer = REFER(data_root, dataset='refclef',  splitBy='berkeley') # 2 train and 1 test images missed
refer = REFER(data_root, dataset='refcoco',  splitBy='unc')
refer = REFER(data_root, dataset='refcoco',  splitBy='google')
refer = REFER(data_root, dataset='refcoco+', splitBy='unc')
refer = REFER(data_root, dataset='refcocog', splitBy='google')   # test split not released yet
refer = REFER(data_root, dataset='refcocog', splitBy='umd')      # Recommended, including train/val/test
```


<!-- refs(dataset).p contains list of refs, where each ref is
{ref_id, ann_id, category_id, file_name, image_id, sent_ids, sentences}
ignore filename

Each sentences is a list of sent
{arw, sent, sent_id, tokens}
 -->
