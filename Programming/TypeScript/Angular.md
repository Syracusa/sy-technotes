# Install Angular
sudo npm install -g @angular/cli


# Import JSON
+ tsconfig.json
```
--- omitted ---
  "compilerOptions": {
    "resolveJsonModule": true, 
    "allowSyntheticDefaultImports" : true,
--- omitted ---
```
+ ts file
```
import DataInfo from '../assets/datainfo.json';
```

# Create Project
ng new {prj-name}

# Using d3
npm install d3 && npm install @types/d3 --save-dev
```
import * as d3 from 'd3'
```

# Using moment
npm install moment
```
import * as moment from 'moment'
```

# Question

+ This code will not works
```   
d3.select('.xaxis')
    .call(xAxis)
    .attr("transform", "translate(" + 0 + ", " + 450 + ")");
```

+ This code works

```
d3.select('.xaxis')
    .append("g")
    .call(xAxis)
    .attr("transform", "translate(" + 0 + ", " + 450 + ")");
```
Why?