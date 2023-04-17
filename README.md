# Missing-Origin
### A python script that loops through folders in a directory looking for origin.yaml files and logging missing ones.

This script recursively looks through all the folders in a directory for origin.yaml files.  If a directory is missing a file it logs it. 
If the it is one directory lower than the starting directory is expects the origin file to be there and adds it to the bad missing origin log. 
Any other folders missing origin files are also logged into the good missing origin log which you can review if you want. This should only contain folders for artwork or multiple discs of a release.

It can handle albums with artwork folders or multiple disc folders in them. It can also handle specials characters and skips and logs any albums that have characters that makes windows fail. It has been tested and works in both Ubuntu Linux and Windows 10.

This script is meant to work in conjunction with other scripts in order to manage a large music library when the source of the music has good metadata you want to use to organize it.  You can find an overview of the scripts and workflow at [Origin-Music-Management](https://github.com/spinfast319/Origin-Music-Management). 

## Dependencies
This project has a dependency on the gazelle-origin project created by x1ppy. gazelle-origin scrapes gazelle based sites and stores the related music metadata in a yaml file in the music albums folder. For this script to work you need to use a fork that has additional metadata including the tags and coverart. The fork that has the most additional metadata right now is: https://github.com/spinfast319/gazelle-origin

## Install and set up
Clone this script where you want to run it.

Set up or specify the two directories you will be using and specify whether you albums are nested under artist or not.
1. The directory of the albums you want to search for missing orgin files in
2. A directory to store the log files the script creates
3. Set the album_depth variable to specify whether you are using nested folders or have all albums in one directory
   - If you have all your ablums in one music directory, ie. Music/Album then set this value to 1
   - If you have all your albums nest in a Music/Artist/Album style of pattern set this value to 2

The default is 1 (Music/Album)

Use your terminal to navigate to the directory the script is in and run the script from the command line.  When it finishes it will output how many album folders are missing origin files that need them as well as how many folders are don't have origin files and likely don't need them.

```
Missing-Origin.py
```

_note: on linux and mac you will likely need to type "python3 Missing-Origin.py"_  
_note 2: you can run the script from anywhere if you provide the full path to it_

It will create logs of any missing origin files it finds and save to the logs folder.
- Logs in the bad-missing-origin.txt file are folders that should have origin files and are missing them.
- Logs in the good-missing-origin.txt file are folders that probably should not have origin files. You can double-check these if you want.
