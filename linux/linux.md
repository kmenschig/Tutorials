
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

<<<<<<< HEAD
##### Combine several pdf files into one

```
pdftk IRS-2016-01.pdf IRS-2016-02.pdf output IRS-2016.pdf
```
=======
##### Replace text in certain lines of file

```
sed -i '44,64s/oldtext/newtext/g' <fileName.txt>
```
>>>>>>> 7995fd81709bfe3f5eea7fcdf37d71b7391e27cb
