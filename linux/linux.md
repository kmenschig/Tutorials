##### Mount other drives, like SSD

```
sudo mount /dev/sdb1 /media/klaus/SSD
```


#### Finding folders or files

##### To find the file file.txt from the root directory upwards

```
find / -name file.txt
```

##### This adds a time stamp to the list when the file was last saved

```
find / -name 'search.txt' printf '%TD %TT %p\n'

```

##### Search for a file from the cwd upwards with time stamp

```
find * -name '*.py' printf '%TD %TT %p\n'
```

##### Write list of files into a text file

```
ls *.csv > list.txt
```

##### Combine several pdf files into one

```
pdftk IRS-2016-01.pdf IRS-2016-02.pdf output IRS-2016.pdf
```

##### Find file 'fvSolution' in folder tree with the exception of folder 'tutorials'

```
find . -path ./tutorials -prune -o -iname fvsolution
```

#### Replace character in xth position of row with another character
##### Below example replace the character '.' in position 13 of line 56 to 87 in blockMeshDict with the character 'x'

```
sed -i '56,87s/^\(.\{13\}\)./\1x/' blockMeshDict

