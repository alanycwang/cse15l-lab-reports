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


