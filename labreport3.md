# Command-line options and alternate ways to use ```find```

## 1: Find by name
Using the option ```-name``` allows you to find files and directories by name. The search is case-sensitive, but you can use ```-iname``` to do a case-insensitive search.

Example 1:
```
alanwang@Alans-MacBook-Pro docsearch % find written_2 -name "chA.txt"
written_2/non-fiction/OUP/Castro/chA.txt
```

Example 2: 
```
alanwang@Alans-MacBook-Pro docsearch % find written_2 -iname "castro"
written_2/non-fiction/OUP/Castro
```

[Source](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/)

## 2: Find with size constraint
You can find files of certain sizes with the ```-size``` option. The ```M```, ```G```, and ```k``` suffixes can be used to represent megabytes, gigabytes, and kilobytes. The ```+``` and ```-``` prefixes indicate whether you are looking for a file larger or smaller than the given number. You can also use multiple find options to search a range.

Example 1:
```
alanwang@Alans-MacBook-Pro docsearch % find written_2 -size -1k
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Rybczynski
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Castro
written_2/travel_guides
written_2/travel_guides/berlitz1/HandRIstanbul.txt
written_2/travel_guides/berlitz1/HandRIbiza.txt
```

Example 2:
```
alanwang@Alans-MacBook-Pro docsearch % find written_2 -size +1k -size -2k
written_2/travel_guides/berlitz1/HandRLasVegas.txt
written_2/travel_guides/berlitz1/HandRHongKong.txt
written_2/travel_guides/berlitz1/HandRLisbon.txt
written_2/travel_guides/berlitz1/HandRMallorca.txt
written_2/travel_guides/berlitz1/HandRLosAngeles.txt
written_2/travel_guides/berlitz1/HandRMadeira.txt
written_2/travel_guides/berlitz1/HandRLakeDistrict.txt
written_2/travel_guides/berlitz1/HandRJerusalem.txt
```

[Source](https://linuxconfig.org/how-to-use-find-command-to-search-for-files-based-on-file-size)

## Find empty files and directories
Use the ```-empty``` option to search for files and directories that are empty. This can be especially useful when clearing up space and deleting unused folders.

Example 1:
```
alanwang@Alans-MacBook-Pro docsearch % find ./ -empty
.//.git/objects/info
.//.git/refs/tags
.//.git/branches
```

Example 2:
```
alanwang@Alans-MacBook-Pro docsearch % find written_2 -empty
```
There is no output as ```written_2``` contains no empty files or folders

[Sourcse](https://askubuntu.com/questions/719912/how-to-find-all-empty-files-and-folders-in-a-specific-directory-including-files)

## Find -type
Use ```-type``` followed by ```d``` or ```f``` to specify a search for directories or files. This is useful when only looking for one of the two types.

Example 1:
```
alanwang@Alans-MacBook-Pro docsearch % find written_2 -type d
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Rybczynski
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Castro
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```

Example 2:
```
alanwang@Alans-MacBook-Pro docsearch % find written_2/non-fiction/OUP -type f
written_2/non-fiction/OUP/Berk/ch2.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/non-fiction/OUP/Berk/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Rybczynski/ch2.txt
written_2/non-fiction/OUP/Rybczynski/ch3.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch3.txt
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch4.txt
written_2/non-fiction/OUP/Kauffman/ch5.txt
written_2/non-fiction/OUP/Kauffman/ch7.txt
written_2/non-fiction/OUP/Kauffman/ch6.txt
written_2/non-fiction/OUP/Kauffman/ch8.txt
written_2/non-fiction/OUP/Kauffman/ch9.txt
written_2/non-fiction/OUP/Kauffman/ch10.txt
written_2/non-fiction/OUP/Fletcher/ch2.txt
written_2/non-fiction/OUP/Fletcher/ch1.txt
written_2/non-fiction/OUP/Fletcher/ch5.txt
written_2/non-fiction/OUP/Fletcher/ch6.txt
written_2/non-fiction/OUP/Fletcher/ch9.txt
written_2/non-fiction/OUP/Fletcher/ch10.txt
written_2/non-fiction/OUP/Castro/chR.txt
written_2/non-fiction/OUP/Castro/chP.txt
written_2/non-fiction/OUP/Castro/chQ.txt
written_2/non-fiction/OUP/Castro/chB.txt
written_2/non-fiction/OUP/Castro/chC.txt
written_2/non-fiction/OUP/Castro/chA.txt
written_2/non-fiction/OUP/Castro/chV.txt
written_2/non-fiction/OUP/Castro/chW.txt
written_2/non-fiction/OUP/Castro/chM.txt
written_2/non-fiction/OUP/Castro/chZ.txt
written_2/non-fiction/OUP/Castro/chL.txt
written_2/non-fiction/OUP/Castro/chN.txt
written_2/non-fiction/OUP/Castro/chY.txt
written_2/non-fiction/OUP/Castro/chO.txt
```

[Source](https://www.tecmint.com/linux-find-command-to-search-multiple-filenames-extensions/)

