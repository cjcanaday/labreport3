# Lab Report 3: Researching Commands

## Command Researched: find

> All commands and flags were found [here](https://www.redhat.com/sysadmin/linux-find-command)

### 1. -iname

This option is similar to the -name flag, but the search is case insensitive.

```console
$ find . -iname "fuNds_shOrtAge.txt"
./government/Media/Funds_Shortage.txt

```

```console
$ find . -iname "CHAPter-*.*.txt"
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
```

Both commands shown above search for text files within the technical directory with mixed cases (both upper and lower). The results that are returned, however, show that the case of the files does not match what was searched for. This demonstrates that the -iname flag could help in a situation where you are unclear as to the casing of the file you are searching for.

### 2. -type

This option allows for the searching of files by type.

```console
$ find . -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos

```

```console
$ find . -type f -iname "*gen*"
./government/Media/BergenCountyRecord.txt
./government/Media/Federal_agency.txt
./government/Media/Greedy_Generous.txt
./government/Media/Service_Agency.txt
./government/Media/agency_expands.txt

```

In the commands shown above, although I am searching through all of .technical, only directories or files are shown, respectively. In the first example, by specifying "d" (standing for directory) after -type, it outputs all directory results. In example 2, searching for anything "gen" in its name, although the folder `./government/Gen_Account_Office` would appear as an output in a typical find, by specifying "f" (standing for file) after -type, it only outputs files. This flag would be very useful in a situation where you are searching either for a file or a directory that are of the same name.


### 3. -maxdepth

This option allows the user to specify how deep of a search they would like to do.

```console
$ find . -maxdepth 2  -iname "*gen*"
./government/Env_Prot_Agen
./government/Gen_Account_Office
```

```console
$ find . -maxdepth 3  -iname "*gen*"
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media/BergenCountyRecord.txt
./government/Media/Federal_agency.txt
./government/Media/Greedy_Generous.txt
./government/Media/Service_Agency.txt
./government/Media/agency_expands.txt
```

These examples demonstrate the differences in searching to different depths. Within the first example, specifying a maxdepth of 2, find only searches within each of the folders in technical, not going beyond that. In the second example however, increasing the maxdepth by one, find now searches the subfolders within `government` finding additional files that match the same search criteria. This flag would be very useful in cases where one has to search a directory with many subdirectories, allowing subdirectories only up to a certain depth to be searched.

### 4. -size

This option allows for the searching of files by the size.

```console
$ find . -size 80b
./biomed/1471-2091-3-18.txt
./biomed/1471-2164-4-21.txt
./biomed/1472-6785-2-7.txt
```

```console
$ find . -size 100b
./biomed/1471-2377-3-4.txt
./biomed/gb-2003-4-3-r20.txt
./biomed/gb-2003-4-6-r39.txt
```
This command takes input of the size of the file in a specified format, and returns files with that specification. In the first example, searching for files in .technical that have a size of 80 bytes, the command returns files of that size. In example two, a similar command is entered except with 100 bytes, which yields different, larger, files which match that specification. This command could be very useful when searching for files that should have a specified size, like text files, or if searching for large files to free up space.

