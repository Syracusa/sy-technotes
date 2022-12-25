# Python
+ Load from json file
```
import json
with open('dump.json', 'r') as f:
    json_dump = json.load(f)
```
+ Dump to json file
```
import json
dict = { "Data" : "myData" }
json_dump = json.dumps(dict, indent=4)
with open("dump.json", "w") as f:
    f.write(json_dump)
```

# Javascript
+ Load from json file
```
fetch('dump.json')
.then((response) => response.json())
.then((json) => console.log(json));
```