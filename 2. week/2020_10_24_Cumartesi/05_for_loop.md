for_loop.sh  
```
#! /bin/bash

for (( i=0; i<10; i++ ))
do
        echo "$i"
done
```
Run script  
```
[train@localhost play]$ ./for_loop.sh
0
1
2
3
4
5
6
7
8
9
```

## inline for loop  
```
[train@localhost play]$ for i in {1..10}; do hostname -f; done
localhost
localhost
localhost
localhost
localhost
localhost
localhost
localhost
localhost
localhost
```

## loop through a directory 
- for_loop_in_directory.sh
```
#!/bin/bash

for file in $(pwd)/*;
  do
    echo $file
  done
```

```
[train@localhost play]$ ./for_loop_in_directory.sh
/home/train/advanced_ds_bigdata/bash_script/play/arguments.sh
/home/train/advanced_ds_bigdata/bash_script/play/bin
/home/train/advanced_ds_bigdata/bash_script/play/closing.sh
/home/train/advanced_ds_bigdata/bash_script/play/conditionals.sh
/home/train/advanced_ds_bigdata/bash_script/play/direction.sh
/home/train/advanced_ds_bigdata/bash_script/play/dns.txt
/home/train/advanced_ds_bigdata/bash_script/play/file_operators2.sh
/home/train/advanced_ds_bigdata/bash_script/play/file_operators.sh
/home/train/advanced_ds_bigdata/bash_script/play/file_operators_test.sh
/home/train/advanced_ds_bigdata/bash_script/play/for_20_sleep.txt
/home/train/advanced_ds_bigdata/bash_script/play/for_loop_in_directory.sh
/home/train/advanced_ds_bigdata/bash_script/play/for_loop.sh
/home/train/advanced_ds_bigdata/bash_script/play/functions.sh
/home/train/advanced_ds_bigdata/bash_script/play/myFile
/home/train/advanced_ds_bigdata/bash_script/play/myFile1
/home/train/advanced_ds_bigdata/bash_script/play/myFile2
/home/train/advanced_ds_bigdata/bash_script/play/myvar1
/home/train/advanced_ds_bigdata/bash_script/play/myvar2
/home/train/advanced_ds_bigdata/bash_script/play/myvar3
/home/train/advanced_ds_bigdata/bash_script/play/myvar4
/home/train/advanced_ds_bigdata/bash_script/play/playfile.txt
/home/train/advanced_ds_bigdata/bash_script/play/read.sh
/home/train/advanced_ds_bigdata/bash_script/play/simple.sh
/home/train/advanced_ds_bigdata/bash_script/play/test.sh
/home/train/advanced_ds_bigdata/bash_script/play/unix
/home/train/advanced_ds_bigdata/bash_script/play/while_loop.sh
```

## loop inside a file iterate lines  
- for_loop_file.sh file
```
#!/bin/bash

for line in $(cat  ~/datasets/insanlar.csv)
  do
    echo $line
  done
```

```
[train@localhost play]$ ./for_loop_file.sh
1,"Gülsüm",35
2,"Cemal",23
3,"Elif",29
4,"Funda",41
5,"Hamza",33
6,"Yalçın",45
7,"Mehmet",44
8,"Gülay",33
9,"Cumhur",38
10,"Burcu",41
11,"Metin",47
12,"Veysel",53
```








- More examples: https://www.cyberciti.biz/faq/bash-for-loop/