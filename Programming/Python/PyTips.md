# Python 

## Comment
+ Multi-line comment
```
"""
{commented statement}
"""
```
## Dict
+ Check existence of key in dict
```
if "key" in d:
    print('key exist')
```
+ Create key with value if not exist
```
d.get('keyname', 'defkeyval')
```
+ iterate dict
```
for k, v in mydict.items():
    pass
```
## File system
### Get directories
```
directories = [d for d in os.listdir(path) if os.path.isdir(os.path.join(path, d))]
for d in directories:
    pass
```
### Get files
```
files = [d for d in os.listdir(path) if os.path.isfile(os.path.join(path, d))]
for d in directories:
    pass
```

### Recursive search
```
for root, dirs, files in os.walk(os.path.join(path, reponame), topdown=True):
    pass
```


## Execute CLI command
```
import subprocess

command = "ls -al"
process = subprocess.run(command, shell=True, check=True, text=True)
```

## String to Bytes
```
def string_to_bytes(s):
    b = bytearray()
    b.extend(s.encode())
    return b
```

## LZMA Compress
```py
import lzma
compresser = lzma.LZMACompressor(format=lzma.FORMAT_ALONE)
compressed = compressor.compress(buf)
compressed += compressor.flush()
decompressed = lzma.LZMADecompressor(format=lzma.FORMAT_ALONE).decompress(compressed)
```