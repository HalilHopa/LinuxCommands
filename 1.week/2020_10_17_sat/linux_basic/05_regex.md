Regular expressions are symbolic notations used to identify patterns in text.

**grep “global regular expression print”** so we can see that grep has something to do with regular
expressions.
`grep "regex_search_term" file_location`

`^`	Start of expression    
`$`	End of expression  
`.` or Dot will match any character  
`[ ]`       will match a range of characters  
`[^ ]`      will match all character except for the one mentioned in braces  
`*`          will match zero or more of the preceding items  
`+`         will match one or more of the preceding items  
`?`         will match zero or one of the preceding items  
`{n}`      will match ‘n’ numbers of preceding items  
`{n,}`     will match ‘n’ number of or more of preceding items  
`{n m}`  will match between ‘n’ & ‘m’ number of items  
`{ ,m}`   will match less than or equal to m number of items  

data: https://raw.githubusercontent.com/erkansirin78/datasets/master/words.txt  

Usage: **grep [OPTION]... PATTERN [FILE]... **
-  `caret (^)` Starts with Erk  
```
[train@localhost play]$ grep ^Erk ~/datasets/words.txt
Erk
Erkan
Erkanıharp
Erke
Erkek
Erkeklenmek
Erkekleşmek
Erkekli
..
..
```
With line numbers
```
[train@localhost ~]$ grep -n ^Erk ~/datasets/words.txt
9870:Erk
9871:Erkan
9872:Erkanıharp
9873:Erke
9874:Erkek
9875:Erkeklenmek
9876:Erkekleşmek
9877:Erkekli
...
...
```

- `$` Ends with kuş 
``` 
[train@localhost play]$ grep kuş$ ~/datasets/words.txt
Akkuş
Baykuş
Boğmaklıkuş
Islıkçıkuş
Karakuş
Kokuş
Sokuş
Yokuş
Şarkıcıkuş  
```

- `.` Includes k.ş there can be anything in place of .
```
[train@localhost play]$ grep "k.ş" ~/datasets/words.txt
Afyonkeş
Afyonkeşlik
Akkuş
Akış
Akışkan
```

- Includes bak  
`[train@localhost play]$ grep bak ~/datasets/words.txt`  

- Ends with kuş but not starts with ak. v: for non-matching, i for case insensitive
```
[train@localhost play]$ grep kuş$ ~/datasets/words.txt | grep -vi ^ak
Baykuş
Boğmaklıkuş
Islıkçıkuş
Karakuş
Kokuş
Sokuş
Yokuş
Şarkıcıkuş
```
- Same but case sensitive  
```
[train@localhost play]$ grep kuş$ ~/datasets/words.txt | grep -v ^ak
Akkuş
Baykuş
Boğmaklıkuş
Islıkçıkuş
Karakuş
Kokuş
Sokuş
Yokuş
Şarkıcıkuş
```

- How many case that mach this filter?   -c, --count print only a count of matching lines per FILE
```
[train@localhost play]$ grep kuş$ ~/datasets/words.txt | grep -vc ^ak
9
```

- T...f starts T and after four character later includes f, there can be any three character in place of ...
```
[train@localhost play]$ grep "T...f" ~/datasets/words.txt
Taaffün
Tahaffuz
Tahaffuzhane
Taraf
Tarafeyn
Tarafgir
```

- Same but we restricted with finish character.
```
[train@localhost play]$ grep "T...f$" ~/datasets/words.txt
Taraf
Tarif
Tavaf
Telef
Telif
Tuhaf
```
- [] Square braces are used to define a range of characters.  
```
[train@localhost play]$ grep M[au]*k ~/datasets/words.txt
Makabil
Makadam
Makak
..
..
Makûs
Muakkip
Mukabele
Mukabeleci
Mukabil
..
..
```

- `[^ ]` This is like the not operator for regex. While using [^ ], it means that our search will include all the characters except the ones mentioned inside the square braces.
Exclude digits
```
[train@localhost play]$ grep [^0-9][A-Za-z] ~/datasets/mixed_tc_kimlik_names_numbers.txt
öbdolhölim öctüzc
öbdollöh ozdoğön
öbdollöh cözödöyi
öbdozöhim öcgül
öbdozzöhmön ogoz
öbdülcödiz öli İpoc
ödom cöyö
ödilo bİçoz
ödnön öğöz
ödnön çolİc
ödnön mondozos cozmön
öhmot böğözön
öhmot cödzi dİcböğ
...
..
```

`*` will match zero or more of the preceding items 
```
[train@localhost play]$ grep Böğ* ~/datasets/words.txt
Bö
Böbrek
Böbreksi
Böbreküstübezi
Böbreğimsi
..
..
Böylemesine
Böylesi
Böylesine
Böğür
Böğürmek
Böğürtlen
Böğürtlenlik
```
- `\` or Escape characters
\ is used when we need to include a character that is a metacharacter or has special meaning to regex. For example, we need to locate all the words ending with a dot, so we can use

- `+` will match one or more of the preceding items  
Starts with Böğ rest can be anything  
```
[train@localhost play]$ grep "Böğ\+" ~/datasets/words.txt
Böğür
Böğürmek
Böğürtlen
Böğürtlenlik
Böğürtmek
Böğürtü
Böğürüş
```
- `{n}`      will match ‘n’ numbers of preceding items  
Will filter words 20 characters excluding digits  
```
[train@localhost play]$ grep "[A-Za-z]\{20\}" ~/datasets/words.txt
Avustralyakaratavuğu
Ayaksızkertenkelegiller
Ayaksızkertenkeleler
Biyolojileştiricilik
Elektroansefalografi
Karikatürleştirilmek
Kişiliksizleştirilme
Kişiliksizleştirilmek
Kuyruksallayangiller
Kırlangıçbalığıgiller
Muhabbetçiçeğigiller
Onikiparmakbağırsağı
Çıngıraklıyılangiller
```
Just select tckn  
```
[train@localhost play]$ grep "[0-9]\{11\}" ~/datasets/mixed_tc_kimlik_names_numbers.txt
35063031338
55060093288
18393291330
86888386210
22938860638
26180015321
```

