# Image Quality Assessment

[![Build Status](https://travis-ci.org/idealo/image-quality-assessment.svg?branch=master)](https://travis-ci.org/idealo/image-quality-assessment)
[![Docs](https://img.shields.io/badge/docs-online-brightgreen)](https://idealo.github.io/image-quality-assessment/)
[![License](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](https://github.com/idealo/image-quality-assessment/blob/master/LICENSE)

This repository provides an implementation of an aesthetic and technical image quality model based on Google's research paper ["NIMA: Neural Image Assessment"](https://arxiv.org/pdf/1709.05424.pdf). You can find a quick introduction on their [Research Blog](https://research.googleblog.com/2017/12/introducing-nima-neural-image-assessment.html).

NIMA consists of two models that aim to predict the aesthetic and technical quality of images, respectively. The models are trained via transfer learning, where ImageNet pre-trained CNNs are used and fine-tuned for the classification task.

For more information on how we used NIMA for our specifc problem, we did a write-up on two blog posts:

* NVIDIA Developer Blog: [Deep Learning for Classifying Hotel Aesthetics Photos](https://devblogs.nvidia.com/deep-learning-hotel-aesthetics-photos/)
* Medium: [Using Deep Learning to automatically rank millions of hotel images](https://medium.com/idealo-tech-blog/using-deep-learning-to-automatically-rank-millions-of-hotel-images-c7e2d2e5cae2)

The provided code allows to use any of the pre-trained models in [Keras](https://keras.io/applications/). We further provide Docker images for local CPU training and remote GPU training on AWS EC2, as well as pre-trained models on the [AVA](https://github.com/ylogx/aesthetics/tree/master/data/ava) and [TID2013](http://www.ponomarenko.info/tid2013.htm) datasets.

Read the full documentation at: [https://idealo.github.io/image-quality-assessment/](https://idealo.github.io/image-quality-assessment/).

Image quality assessment is compatible with Python 3.6 and is distributed under the Apache 2.0 license. We welcome all kinds of contributions, especially new model architectures and/or hyperparameter combinations that improve the performance of the currently published models (see [Contribute](#contribute)).


## Trained models
| <sub>Predictions from aesthetic model</sub>
| :--:
| ![](readme_figures/images_aesthetic/aesthetic1.jpg_aesthetic.svg)


| <sub>Predictions from technical model</sub>
| :--:
| ![](readme_figures/images_technical/techncial3.jpgtechnical.svg)




We provide trained models, for both aesthetic and technical classifications, that use MobileNet as the base CNN. The models and their respective config files are stored under `models/MobileNet`. They achieve the following performance

Model      | Dataset | EMD  | LCC | SRCC  
----- |  ------- | ---  | --- | ----  
MobileNet aesthetic | AVA | 0.071 |0.626|0.609
MobileNet technical | TID2013 | 0.107 |0.652|0.675


## Predict

    python3 ./evaluater/predict.py --base-model-name 'MobileNet' --weights-file '../models/MobileNet/weights_mobilenet' --image-source './img.jpg'



## Cite this work
Please cite Image Quality Assessment in your publications if this is useful for your research. Here is an example BibTeX entry:
```BibTeX
@misc{idealods2018imagequalityassessment,
  title={Image Quality Assessment},
  author={Christopher Lennan and Hao Nguyen and Dat Tran},
  year={2018},
  howpublished={\url{https://github.com/idealo/image-quality-assessment}},
}
```

## Maintainers
* Christopher Lennan, github: [clennan](https://github.com/clennan)
* Hao Nguyen, github: [MrBanhBao](https://github.com/MrBanhBao)
* Dat Tran, github: [datitran](https://github.com/datitran)

## Copyright

See [LICENSE](LICENSE) for details.
