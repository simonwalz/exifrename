# exifrename

A perl script to rename pictures with their EXIF CreateData entry.

The script depends on [exiftool](http://www.sno.phy.queensu.ca/~phil/exiftool/).

## Usage

```sh
exifrename [-db dbfile] [-append append] [-format format] [-test] files
```

Example: ``exifrename *.JPG *.THM``

  * `-db dbfile` File with list of already used filenames. New filenames will be added.
  * `-append s` String or char to be appended to the filename.
  * `-format f` Format of the new base filename (like unix function date), Default: `%Y_%m_%d-%H_%M_%S`.
  * `-test` test, no action.
  * `-` get files from STDIN.

## Hints

Command to correct all EXIF timestamps:
(in this example set the timestamps by 1h, 5min and 26sec into the past)

```sh
exiftool "-AllDates-=0:0:0 1:05:26" -overwrite_original .
```

## exifrotate

This repository contains an addional script to rotate pictures using their EXIF orientation flag.

```sh
exifrotate [files.jpg]
```

## Alternatives

Use exiftool with the following parameters (see [exiftool documentation](http://www.sno.phy.queensu.ca/~phil/exiftool/filename.html))

```sh
exiftool -d %Y_%m_%d-%H_%M_%S%%-c.%%e "-filename<CreateDate" .
```

