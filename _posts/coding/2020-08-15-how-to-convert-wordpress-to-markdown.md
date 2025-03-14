---
date: 2020-08-15
title: How to convert wordpress to markdown
category: coding
---

### Convert wordpress export.xml to markdown files

1. Wordpress export xml
1. convert export.xml to markdown files (no year, no day, no folder for each post, date prefix, not download images)

```bash
$ npx wordpress-export-to-markdown
npx: installed 137 in 11.812s

Starting wizard...
? Path to WordPress export file? wordpress.xml
? Path to output folder? output
? Create year folders? No
? Create month folders? No
? Create a folder for each post? No
? Prefix post folders/files with date? Yes
? Save images attached to posts? Yes
? Save images scraped from post body content? Yes
```



### Get `pinyin.txt`

1. print all file title and save as file `title.txt`

```
for f in *;
do sed -n 2p $f; done;
```

1. use vim to remove title line prefix and suffix
1. use php-pinyin-converter to convert titles to pinyin

```
while read -r line; do
	php convert.php $line
done < title.txt
```

1. save pinyin titles to file `pinyin.txt`

### Generate `date.txt`

1. Print all file date  
```
for f in *;
  do sed -n 3p $f;
done;
```
1. use vim to remove date line prefix and suffix

### Rename files to pinyin

1. rename files to pinyin

```
i=1;
j=1;
for f in *;
do
mv $f $(sed -n $(echo $i)p ../date)-$(sed -n $(echo $j)p ../out.cv).md
((i=i+1))
((j=j+1));
done
```
