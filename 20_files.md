# Files

## disk

List directory & file size
```sh
du -sh *
```

List directory & file size, sort by size descending
```sh
du -sh * | sort -rh
```

## tar

Compress
```sh
tar -cvf archive.tar directory
```

Compress using gzip
```sh
tar -cvzf archive.tar.gz directory
```

Extract
```sh
tar -xvf archive.tar
```

Extract (automatically detect the compression type: gzip, bzip2, etc.)
```sh
tar -xvf archive.tar.gz
```

Extract gzipped tar (explicit)
```sh
tar -xvzf archive.tar.gz
```

## zip

```sh
zip -r archive.zip directory
```

```sh
unzip archive.zip
```
