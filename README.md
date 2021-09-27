# Urban-Tree-Cover-Dataset-UTCD-

# Description

In UTCD, the high resolution urban tree labels were uniformly sampled at urban area of Guangdong province, China, as shown in Fig. 1. Different from the homogeneously distributed trees that are easily identified, urban tree covers usually consist of greenbelt, horticulture, arboriculture, ornamental, and commonly distributed along road, in grassland areas, in public spaces such as residential, commercial, schools, hospitals, parks, transportation station, industrial, or in private gardens, which is highly entangled with anthropology (shown in Fig. 1). With full consideration of these circumstances, these fragmented urban trees were carefully delineated on Google Earth images downloaded at 2m spatial resolution during 2019 by surveying and mapping experts. Furthermore, field survey was also conducted for further validation. Generally, vegetation that higher than 5m can be defined as trees according to FAO, to distinguish it from grassland or shrub (Bunting and Lucas, 2006). Finally, 1946 patches of size 640×640 were cropped from the annotated images at sample sites in Guangdong. The statistics of the annotated urban tree pixels and non-tree pixels are 0.1321 billion and 0.6650 billion, respectively. In addition, the annotations were examined by third party without participated in annotation works, for a further refinement.

As for LR image, Sentinel-2 images at 10m spatial resolution in 2019 were considered. It is freely and readily available from data center of European Space Agency (ESA) (https://glovis.usgs.gov/), which contain 13 spectral bands at 10 m, 20m and 60m spatial resolution with a 5-day revisit period (Drusch et al., 2012). These images were preprocessed with atmospherically correction, geometrically correction (https://developers.google.com/ earth-engine/datasets/catalog/COPERNICUS_S2#description), and were rectified to the Universal Transverse Mercator (UTM) projection system (Datum WGS84). Seven bands are selected, i.e., band1~band4, band8, band11, band12, and were uniformly resampled to 10 m. Furthermore, in order to eliminate influence of phenology feature of evergreen and deciduous tree, all Sentinel-2 images throughout 2019 that less than 10% cloud contamination were merged by median-mosaic composition . The Sentinel-2 images were also sampled at exactly the same footprint of label images to guarantee a co-registered relation between them, and also 1946 patches with size of 128×128 were cropped. The reconstruction scale between Sentinel-2 image and label image is 5. In order for training and testing of a DLSMNet, the UTCD is preliminarily split into training set, validation set and test set, with patches of 1383, 195, 368 patch pairs, respectively. 


![样本示意图](https://user-images.githubusercontent.com/44233952/134940726-34d83380-480f-4e2a-9aaa-f2a082d1cf59.png)



UTCD dataset is publicly available:

Google Drive: https://drive.google.com/file/d/1ESehycWZkHX7IiU69wba1gglMjRsUoIr/view?usp=sharing


# How to Use

This dataset is in ENVI format, which can be read by matlab code provide in freadenvi.m.

```python
[img,shp,~]=freadenvi(img_path);
% img=reshape(img,shp(1),shp(2),shp(3));
% img=permute(img,[2,1,3]);
```

Besides, it can be also read by Python:

```python
import spectral
img = spectral.open_image(img_path).load()
```

# Citation

If you use any part of this dataset in your research, please cite our paper:
```
@article{
author = {Da He, Qian Shi, Xiaopin Liu, and Yanfei Zhong},
journal = {International Journal of Applied Earth Observation and Geoinformation},
title = {{Generating 2m fine-scale urban tree cover product over 34 metropolises in China based on deep global context aware sub-pixel mapping network}},
url = {},
year = {2021}
}
```
