# ImageNet 1K Bounding Boxes
For some experiments, you might wanna pass only the `background` of imagenet images vs passing only the foreground. Here, I've included the code to extract the meta-data for the bounding box, cleaning up the the downloaded stuff, and then changing ImageNet Loader to support only the images that have box annotations. 




# Restarting from the scratch
Downloading:
First download the data from [https://image-net.org/data/bboxes_annotations.tar.gz](here):
```
wget "https://image-net.org/data/bboxes_annotations.tar.gz"
```

Extract the File:
```
tar -xvf bboxes_annotations.tar.gz 
```

Extract every subfolder:
```
cd bboxes_annotations
ls | grep .tar.gz | while read f ; do tar -xvf "${f}" ; done
```

Convert dataset to JS:
```
python read_xml.py 
```

Clean the extra 50GB extracted files:
```
rm *.tar.gz
ls | grep "n.*" | while read f ; do rm -rf "${f}"  ; done 
```
