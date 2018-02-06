![Banner](https://steemit-production-imageproxy-thumbnail.s3.amazonaws.com/DQmcu5iqy5qycEpxrnnb64XNMueSDAfNenyM9nHJsEgdpLo_1680x8400)

# FGVCx Fungi Classification Challenge
Please open an issue if you have questions or problems with the dataset.

# 2018 Competition
The 2018 competition, sponsored by Svampe Atlas, is part of the [FGVC^5 workshop](http://fgvc.org) at [CVPR](http://cvpr2018.thecvf.com/).

## Kaggle
We are using Kaggle to host the leaderboard. Checkout the competition page [here](https://www.kaggle.com/).

## Dates
|||
|------|---------------|
Data Released|April 15, 2018|
Submission Deadline|June 11, 2018|
Winners Announced|June 18, 2018|

## Details

(TBD)

There are a total of 3,000 species in the dataset, with ? training images and ? validation images. For the training set, the distribution of images per category follows the observation frequency of that category by the ? community. Therefore, there is a non-uniform distribution of images per category. Example images, along with their unique [GBIF](http://www.gbif.org/) ID numbers, can be viewed [here](https://docs.google.com/spreadsheets/d/1JHn6J_9HBYyN5kaVrH1qcc3VMyxOsV2II8BvSwufM54).


| Super Category |	Category Count	| Train Images |	Val Images |
|------|---------------|-------------|---------------|
Mushroom|0|0|0|
|||||
|Total|0|0|0|


## Evaluation
We follow a similar metric to the classification tasks of the [ILSVRC](http://image-net.org/challenges/LSVRC/2016/index#scene). For each image <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/77a3b857d53fb44e33b53e4c8b68351a.svg?invert_in_darkmode" align=middle width=5.642109pt height=21.60213pt/>, an algorithm will produce 5 labels <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/655bedbaf4a65f397b5041d0fdecde4c.svg?invert_in_darkmode" align=middle width=15.601905pt height=22.74591pt/>, <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/6d0aa77223bd2246e5cdd2a422d9e584.svg?invert_in_darkmode" align=middle width=82.4274pt height=21.60213pt/>. We allow 5 labels because some categories are disambiguated with additional data provided by the observer, such as latitude, longitude and date. It might also be the case that multiple categories occur in an image (e.g. a photo of a bee on a flower). For this competition each image has one ground truth label <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/681a37b53b66acbc455e39ca3e6f1c41.svg?invert_in_darkmode" align=middle width=12.444795pt height=14.10255pt/>, and the error for that image is:
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/7a42826f81c53c77e0fef3c827238d25.svg?invert_in_darkmode" align=middle width=123.403665pt height=24.865665pt/></p>
Where
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/7a45c501d5042bd031a267f008fa2ae6.svg?invert_in_darkmode" align=middle width=190.2021pt height=49.13139pt/></p>

The overall error score for an algorithm is the average error over all <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode" align=middle width=14.94405pt height=22.38192pt/> test images:
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/444adcac0c7cbb4a8419ee1484625349.svg?invert_in_darkmode" align=middle width=118.05123pt height=41.069655pt/></p>

## Guidelines

Participants are restricted to train their algorithms on FGVCx Fungi Challenge train and validation sets. Pretrained models may be used to construct the algorithms (e.g. ImageNet pretrained models) as long as participants do not actively collect additional data for the target categories of the iNaturalist 2017 competition. Please specify any and all external data used for training when uploading results.

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
12345,0 78 23 3 42
67890,83 13 42 0 21
```
The `id` column corresponds to the test image id. The `predicted` column corresponds to 5 category ids, separated by spaces. You should have one row for each test image.

## Terms of Use

(TBD)

By downloading this dataset you agree to the following terms:

1. You will abide by the [iNaturalist Terms of Service](https://www.inaturalist.org/pages/terms)
2. You will use the data only for non-commercial research and educational purposes.
3. You will NOT distribute the above images.
4. The ? makes no representations or warranties regarding the data, including but not limited to warranties of non-infringement or fitness for a particular purpose.
5. You accept full responsibility for your use of the data and shall defend and indemnify the ?, including its employees, officers and agents, against any and all claims arising from your use of the data, including but not limited to your use of any copies of copyrighted images that you may create from the data.

## Data

(TBD) 

Download the dataset files here:
  * [Training and validation images [?GB]](https://svampe.databasen.org)
      * Alternate links for different parts of the world:
          * TBD 
      * Running `md5sum` on the tar.gz file should produce `7c784ea5e424efaec655bd392f87301f  train_val_images.tar.gz`
      * Images have a max dimension of 800px and have been converted to JPEG format
      * Untaring the images creates a directory structure like `train_val_images/super category/category/image.jpg`. This may take a while.

