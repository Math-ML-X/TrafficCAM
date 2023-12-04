## The dataset (TrafficCAM) can be downloaded from the links below:
The fully annotated data can be downloaded at:  
Fully_annotate.zip https://drive.google.com/file/d/1h4oUqECDF05vSYMkYgz0aUc_RRzHlh3e/view?usp=sharing  

The first frame annotated data is divided into 3 partitions:  
Partition 1:  
FirstFrame_annotate-1.zip https://drive.google.com/file/d/1lYz_aBX-4Ygj-tbUkHvsaPB3vxOIvGBA/view?usp=sharing  
Partition 2:   
FirstFrame_annotate-2.zip https://drive.google.com/file/d/1TmN07tdC5NYpcIPI5tmhOrU1XfK7Yu6V/view?usp=share_link  
Partition 3:   
FirstFrame_annotate-3.zip https://drive.google.com/file/d/1cKOpDQ-NvqTxIETXYcDOv_Ojc3UZm2Qq/view?usp=sharing

## The data structure for using the dataset as suggested in benchmark can be viewed below:
      ├── TrafficCAM
        ├── raw
          ├── FirstFrame_annotate
            ├── [Video1_ID]
            :  ├── frame0.json   	# annotation of frame0 (under FirstFrame_annotate only the 1st frame is annotated)
            :  ├── frame0.jpg	# raw frame0
            :  ├── frame2.jpg	# raw frame2
            :  :
            :  :	### 30 raw frames per video 
            :  :	### NOTE: in video "BLR_1651662434.7875617", only 23 raw frames: missed frame6,8,50,52,54,56,58.
            :	 :		        
            :  └── frame58.jpg	# raw frame58
            :
            :	### 2024 videos with only first frame annotated in total
            :
            └──  [Video2024_ID] 	 
          └── Fully_annotate
            ├── [Video1_ID]
            :  ├── frame0.json   	# annotation of frame0
            :  :
            :  :	 ### 30 annotated frames in total (under Fully_annotate all frames annotated)
            :  :
            :  ├── frame58.json	# annotation of frame58
            :  ├── frame2.jpg	# raw frame2
            :  :
            :  :	 ### 30 raw frames in total
            :  :
            :  └── frame58.jpg	# raw frame58
            :	
            :	### 78 videos with all frames annotated in total
            :	
            └──  [Video78_ID]
       
        └── splits          # official splits
          ├── benchmark     # training set, (validation set), and test set used in benchmark
            ├── train
                ├── semi-supervised
                    ├── 1_27
                        ├── train_labelled.txt
                        └── train_unlabelled.txt
                    ├── 1_54
                      ├── train_labelled.txt
                      └── train_unlabelled.txt
                    ├── 1_108
                      ├── train_labelled.txt
                      └── train_unlabelled.txt
                    └──1_216
                      ├── train_labelled.txt
                      └── train_unlabelled.txt
                └── supervised
                    └──  train.txt
            ├── val.txt
            └── test.txt
          └── leave-out.txt			# 12 fully annotated videos are left out for other use




## The benchmarked split in semi-supervised training can be found in:
splits.zip https://drive.google.com/file/d/1GcQ3J56kU-6TwRqRjzvI28-OF6QUdHeR/view?usp=sharing


## Instruction for downloading and assembling the data as benchmarked is as below through commend lines:

### Create a clean folder
```
mkdir TrafficCAM
cd TrafficCAM
mkdir raw
cd raw
```

### Download the data
```
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1lYz_aBX-4Ygj-tbUkHvsaPB3vxOIvGBA' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1lYz_aBX-4Ygj-tbUkHvsaPB3vxOIvGBA" -O FirstFrame_annotate-1.zip && rm -rf /tmp/cookies.txt 
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1TmN07tdC5NYpcIPI5tmhOrU1XfK7Yu6V' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1TmN07tdC5NYpcIPI5tmhOrU1XfK7Yu6V" -O FirstFrame_annotate-2.zip && rm -rf /tmp/cookies.txt
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1cKOpDQ-NvqTxIETXYcDOv_Ojc3UZm2Qq' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1cKOpDQ-NvqTxIETXYcDOv_Ojc3UZm2Qq" -O FirstFrame_annotate-3.zip && rm -rf /tmp/cookies.txt
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1h4oUqECDF05vSYMkYgz0aUc_RRzHlh3e' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1h4oUqECDF05vSYMkYgz0aUc_RRzHlh3e" -O Fully_annotate.zip && rm -rf /tmp/cookies.txt
```

### Unzip the folders
```
sudo apt install unzip
unzip FirstFrame_annotate-1.zip
unzip FirstFrame_annotate-2.zip
unzip FirstFrame_annotate-3.zip
unzip Fully_annotate.zip
```

### Assemble the first frame annotated data:
```
mkdir FirstFrame_annotate
mv FirstFrame_annotate-1/* FirstFrame_annotate-2/* FirstFrame_annotate-3/* FirstFrame_annotate/
```

### Download the benchmarked splits
```
cd ../
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1GcQ3J56kU-6TwRqRjzvI28-OF6QUdHeR' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1GcQ3J56kU-6TwRqRjzvI28-OF6QUdHeR" -O splits.zip && rm -rf /tmp/cookies.txt 
unzip splits.zip
```

### Delete all preparation files
```
rm raw/*.zip
rm -r raw/*-*
rm *.zip
rm -r __MACOSX
```
