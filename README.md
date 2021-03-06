# DynWalls - MacOS Wallpapers on Linux

This Python programs allows you to set Dynamic Wallpapers from MacOS (in the [HEIC](https://en.wikipedia.org/wiki/High_Efficiency_Image_File_Format) format) as your background.

## Features
 - Read HEIC file and set wallpaper
 - Update wallpaper at times specified in the HEIC file
 - Wallpaper updating command can be specified

### Missing Features
 - HEIC files using the sun position are currently not supported, but hopefully in the future


## Requirements
 - Systemd (For automatic updating)
 - exiftool
 - libheif 
 
 Note that both `exiftool` and `heif-convert`(part of libheif) have to be in your PATH.
 
## Installation
Currently, the program is not available on pypi and has to be cloned manually.
After that you can use
```shell
python3 path/to/cloned/repo/dynwalls
```
to run the program.


## Usage
First, specify a command that will set your wallpaper given a jpg image:

```shell
dynwalls setcmd 'feh --bg-fill --no-fehbg {}'
```

You can use a custom shellscript for more complicated setups, just make sure it is available in your PATH.


Then, specify a dynamic wallpaper to use:

```shell
dynwalls use mojave.heic
```

This will install a systemd user service and a systemd timer which are not yet activated.

Sadly, wallpapers that use the sun position are not yet supported. The program will tell you if the passed picture is not supported.


Then, enable automatic updating of your wallpaper:

```shell
dynwalls enable
```

This will activate the systemd timer.


If you want to disable the automatic updating use:

```shell
dynwalls disable
```


## Troubleshooting
You can run 
```shell
journalctl --user -u dynamicwalls
```
to see possible error messages.
