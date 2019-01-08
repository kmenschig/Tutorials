
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

