## Summary
A simple LSTM network for purely temporal classification

## How to run the code:

1. Download the data, collect its path and update it in ```config-gs.ini``` folder.

**NOTE:** Current implementation assumes that the NAIP folder is named as ```filtered-extracts-subset``` and the MODIS folder is named as ```filtered-extracts-subset-ts``` for the dataloader to work.

2. To run training/gridsearch cd to each folder and do:
 
 ```python3 train_gridsearch.py --config '.config file name' --task 'task name'```


* ```--config``` refers to the config file
* ```--task``` here refers to the header in the config file. 
* You can specify the parameters in the ```train_gridsearch.py``` file. For each combination of parameters specified in ```train_gridsearch.py```, it generates a model as per specifications and saves it to disk.

3. Note that the models are given names based on timestamp when the training was started. This gives us easy way to check which hyperparameters in grid gave best result and choose that for prediction. For each run, the training losses etc are all saved using this time stamp, for easy correlation. 

4. To change configuration parameters like input/output paths etc. update them in config file

5. To evalulate a particular model, update the training model file names you created above in the first few lines of ```predict_multi.py``` and run the code as shown below: 
``` python3 predict_multi.py --config 'config file name' --task 'task name'```

6. You can generate the csvs for svm fusion for the lstm network here by following same procedure as for prediction. This saves csvs for train, val and test predicted probabilites. Copy these files over to the svm-fusion folder before trying svm fusion.
``` python3 predict_for_fusion.py --config 'config file name' --task 'task name'``` 
