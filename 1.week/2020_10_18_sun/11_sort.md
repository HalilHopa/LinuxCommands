The sort program sorts the contents of standard input, or one or more files
specified on the command line, and sends the results to standard output.
  
1. Create a file  
```
[train@localhost linux]$ cat <<EOF > sortfile
> ali
> mahmut
> cemal
> gizem
> burcu
> EOF
```
2. Without sorting  
```
[train@localhost linux]$ cat sortfile
ali
mahmut
cemal
gizem
burcu
```

3. with sort
```
[train@localhost linux]$ sort < sortfile
ali
burcu
cemal
gizem
mahmut
```

4. Reverse sort 
```
[train@localhost linux]$ sort -r < sortfile
mahmut
gizem
cemal
burcu
ali
```

5. Add new field to sortfile
```
[train@localhost linux]$ cat <<EOF > sortfile
ali;33
mahmut;25
cemal;41
gizem;27
burcu;33
EOF

[train@localhost linux]$ cat sortfile
ali;33
mahmut;25
cemal;41
gizem;27
burcu;33
```

6. Order to age column   
```
[train@localhost linux]$ sort -t\; -k2 < sortfile
mahmut;25
gizem;27
ali;33
burcu;33
cemal;41
```

7. Reverse order age
```
[train@localhost linux]$ sort -t\; -k2 -r < sortfile
cemal;41
burcu;33
ali;33
gizem;27
mahmut;25
```

8. Same but different notation
```
[train@localhost linux]$ cat sortfile |  sort -t\; -k2 -r
cemal;41
burcu;33
ali;33
gizem;27
mahmut;25
```

`-t` is for seperator   
`-k` is for column index (starts from 1)  
Content will be considered as string  
