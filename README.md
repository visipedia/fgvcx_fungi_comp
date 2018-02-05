![Banner](https://steemit-production-imageproxy-thumbnail.s3.amazonaws.com/DQmcu5iqy5qycEpxrnnb64XNMueSDAfNenyM9nHJsEgdpLo_1680x8400)

# FGVCx Fungi Classification Challenge
Please open an issue if you have questions or problems with the dataset.

# 2018 Competition
The 2018 competition, sponsored by Svampe Atlas, is part of the [FGVC^4 workshop](http://fgvc.org) at [CVPR](http://cvpr2018.thecvf.com/).

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
We follow a similar metric to the classification tasks of the [ILSVRC](http://image-net.org/challenges/LSVRC/2016/index#scene). For each image $i$, an algorithm will produce 5 labels $l_{ij}$, $j=1,\ldots,5$. We allow 5 labels because some categories are disambiguated with additional data provided by the observer, such as latitude, longitude and date. It might also be the case that multiple categories occur in an image (e.g. a photo of a bee on a flower). For this competition each image has one ground truth label $g_i$, and the error for that image is:
$$
e_i = \min_{j}d(l_{ij}, g_i)
$$
Where
$$
d(x, y) =
\begin{cases}
    0       & \quad \text{if } x = y \\
    1  & \quad \text{otherwise}\\
\end{cases}
$$

The overall error score for an algorithm is the average error over all $N$ test images:
$$
\text{score} = \frac{1}{N} \sum_{i} e_{i}
$$

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

