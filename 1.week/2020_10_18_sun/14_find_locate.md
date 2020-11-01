1. locate and find helps us search and find files   
while locate uses a db located in `/var/lib/mlocate/mlocate.db` find search directly in filesystem.

2. locate   
```
[train@localhost play]$ locate Advertising.csv
/home/train/datasets/Advertising.csv
/home/train/production_level_ds/linux_basic/play/Advertising.csv.gz
```

3. find 
```
[train@localhost play]$ find /home/train/ -name "Advertising.*"
/home/train/datasets/Advertising.csv
/home/train/production_level_ds/linux_basic/play/Advertising.csv.gz
```
