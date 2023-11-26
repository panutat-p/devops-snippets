# Files

## tar

Compress
```shell
tar -cvf archive.tar directory
```

Compress using gzip
```shell
tar -cvzf archive.tar.gz directory
```

Extract
```shell
tar -xvf archive.tar
```

Extract (automatically detect the compression type: gzip, bzip2, etc.)
```shell
tar -xvf archive.tar.gz
```

Extract gzipped tar (explicit)
```shell
tar -xvzf archive.tar.gz
```
