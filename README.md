![Banner](https://raw.githubusercontent.com/visipedia/fgvcx_fungi_comp/master/assets/fungi_cover.jpg)

# 2018 FGVCx Fungi Classification Challenge
The 2018 competition is part of the [FGVC^5 workshop](https://sites.google.com/view/fgvc5/home) at [CVPR](http://cvpr2018.thecvf.com/).
Our sponsor, the [Svampe Atlas](https://svampe.databasen.org/), has provided a dataset from a carefully curated database containing over 100,000 fungi images. The Svampe Atlas has a comprehensive representation of nearly 1,500 wild mushrooms species which have been spotted and photographed by the general public in Denmark.

Please open an issue if you have questions or problems with the dataset.

## Kaggle
We are using Kaggle to host the leaderboard. Checkout the competition page [here](https://www.kaggle.com/c/fungi-challenge-fgvc-2018).

## Dates
|||
|------|---------------|
Data Released|April 1, 2018|
Submission Deadline|June 11, 2018|
Winners Announced|June  22, 2018|

## Details

There are a total of 1,394 fungi species in the dataset, with 85,578 training images and 4,182 validation images. The testing set contains 9,758 images. All images are sourced from fungi species submitted in the Danish Svampe Atlas and example images can be viewed [here](https://svampe.databasen.org/).

## Evaluation
We follow a similar metric to the classification tasks of the [ILSVRC](http://image-net.org/challenges/LSVRC/2016/index#scene). For each image <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/77a3b857d53fb44e33b53e4c8b68351a.svg?invert_in_darkmode" align=middle width=5.642109pt height=21.60213pt/>, an algorithm will produce 3 labels <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/655bedbaf4a65f397b5041d0fdecde4c.svg?invert_in_darkmode" align=middle width=15.601905pt height=22.74591pt/>, <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/946e592e2b2753a9272767ae3dd5b9a9.svg?invert_in_darkmode" align=middle width=82.4274pt height=21.60213pt/>. For this competition each image has one ground truth label <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/681a37b53b66acbc455e39ca3e6f1c41.svg?invert_in_darkmode" align=middle width=12.444795pt height=14.10255pt/>, and the error for that image is:
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/7a42826f81c53c77e0fef3c827238d25.svg?invert_in_darkmode" align=middle width=123.403665pt height=24.865665pt/></p>
Where
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/7a45c501d5042bd031a267f008fa2ae6.svg?invert_in_darkmode" align=middle width=190.2021pt height=49.13139pt/></p>

The overall error score for an algorithm is the average error over all <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode" align=middle width=14.94405pt height=22.38192pt/> test images:
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/444adcac0c7cbb4a8419ee1484625349.svg?invert_in_darkmode" align=middle width=118.05123pt height=41.069655pt/></p>

## Guidelines

Participants are restricted to train their algorithms on the 2018 FGVCx Fungi Classification competition train and validation sets. Pretrained models may be used to construct the algorithms (e.g. ImageNet pretrained models) as long as participants do not actively collect additional data for the target species in the 2018 FGVCx Fungi Classification competition. Please specify any and all external data used for training when uploading results.

The general rule is that we want participants to use only the provided training and validation images to train a model to classify the test images. We do not want participants crawling the web in search of additional data for the target categories. Participants should be in the mindset that this is the only data available for those categories.

Participants are allowed to collect additional annotations (e.g. bounding boxes) on the provided training and validation sets. Teams should specify that they collected additional annotations when submitting results.

## Annotation Format
We closely follow the annotation format of the [COCO dataset](http://mscoco.org/dataset/#download). The annotations are stored in the [JSON format](http://www.json.org/) and are organized as follows:
```
{
  "info" : info,
  "images" : [image],
  "categories" : [category],
  "annotations" : [annotation],
  "licenses" : [license]
}

info{
  "year" : int,
  "version" : str,
  "description" : str,
  "contributor" : str,
  "url" : str,
  "date_created" : datetime,
}

image{
  "id" : int,
  "width" : int,
  "height" : int,
  "file_name" : str,
  "license" : int,
  "rights_holder" : str
}

category{
  "id" : int,
  "name" : str,
  "supercategory" : str,
}

annotation{
  "id" : int,
  "image_id" : int,
  "category_id" : int
}

license{
  "id" : int,
  "name" : str,
  "url" : str
}
```

## Submission Format

The submission format for the Kaggle competition is a csv file with the following format:
```
id,predicted
12345, 23 3 42
67890, 42 0 21
```
The `id` column corresponds to the test image id. The `predicted` column corresponds to 3 category ids, separated by spaces. You should have one row for each test image.

## Terms of Use

By downloading this dataset you agree to the following terms:

1. You will abide by the [Danish Svampe Atlas Terms of Service](https://svampe.databasen.org/citation)
2. You will use the data only for non-commercial research and educational purposes.
3. You will NOT distribute the above images.
4. The Danish Svampe Atlas makes no representations or warranties regarding the data, including but not limited to warranties of non-infringement or fitness for a particular purpose.
5. You accept full responsibility for your use of the data and shall defend and indemnify the Danish Svampe Atlas, including its employees, officers and agents, against any and all claims arising from your use of the data, including but not limited to your use of any copies of copyrighted images that you may create from the data.

## Data

Download the dataset files here:
  * [Training and validation images [13GB]](https://labs.gbif.org/fgvcx/2018/fungi_train_val.tgz)
      * Running `md5sum fungi_train_val.tgz` on the tgz file should produce `df2b2980835668ed1d9a0e286e4bdadd`
      * Images have a max dimension of 1024px and have been converted to JPEG format
      * Untaring the images creates a directory structure like `images/category/image.jpg`. This may take a while.

  * [Testing images [1.3GB]](https://labs.gbif.org/fgvcx/2018/fungi_test.tgz)
      * Running `md5sum fungi_test.tgz` on the tgz file should produce `949fc7266f7c6574e4ce359cf2571c85`
      * Images have a max dimension of 1024px and have been converted to JPEG format
      * Untaring the images creates a directory structure like `test/image.jpg`. This may take a while.

  * [Training and validation annotations [2.9MB]](https://labs.gbif.org/fgvcx/2018/train_val_annotations.tgz)
      * Running `md5sum train_val_annotations.tgz` on the tgz file should produce `c3c0f1b8a8d0b60619c43d9c89bdbc7e`
  
  * [Testing image information [90K]](https://raw.githubusercontent.com/visipedia/fgvcx_fungi_comp/master/data/test_information.tgz)
      * Running `md5sum test_information.tgz` on the tgz file should produce `8c4bc9c9a0e3d6f1c1fd24ee4141c86f`

