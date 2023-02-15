## Generating random binary files
To generate random files, the following shell command can be used:
- `of`:    the name of the binary file to be created
- `count`: the number of bytes

```bash
$ dd if=/dev/urandom of=myfile.bin bs=1 count=1024
```
