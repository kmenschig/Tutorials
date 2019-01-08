
### Finding folders or files

###### To find the file file.txt from the root directory upwards

```
find / -name file.txt
```

###### This adds a time stamp to the file search

```
find / -name 'search.txt' printf '%TD %TT %p\n'
```

