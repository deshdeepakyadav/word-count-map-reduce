wordcount with MapReduce with Hadoop streaming utils for NodeJS
-----------------------------------------------------------------------

This example uses a set of hadoop streaming functions, which allows to easily integrate word count functions.

### To run the example program locally

	- Install NodeJS (assuming windows OS locally)
	- Clone this repository in local from (https://github.com/deshdeepakyadav/word-count-map-reduce.git)
	- run `npm install` [Dependent packages for this utility program is added under package.json]
	- go to "input" directory and put your content which needs to word count in text file
	- open cmd and run this command with input text file as an argument `mapreduce-script.bat .\input\<filename>`
	- wordcount output file from map-reduce gets saved into "output" directory, examine the results
	- wordcount is mapped to each unique word in the document

### Functions supported by hadoop streaming utility

Hadoop streaming functions are included as a library under "lib" directory - hadoop-streaming-utils.js. Hadoop streaming functions contains a set of utils to read & process data line by line. The next line is read only after finishing processing the previous one. Also supports async file reads where the reduce function needs to return a promise. 

**iterateLines**

Will read and process input line by line.

```
hadoopUtils.iterateLines(function(data) {  });
```

**iterateJsonLines**

Will read input line by line and will apply JSON.parse to each line.

```
hadoopUtils.iterateJsonLines(function(data) {  });
```

**iterateKeysWithJsonValues**

1. Reads input line by line. 
2. Extracts key and value from line. 
3. Applies JSON.parse to value.

```
hadoopUtils.iterateKeysWithJsonValues(function(key, value) { });
```

**iterateKeysWithGroupedJsonValues**

1. Reads input line by line. 
2. Extracts key and value from line. 
3. Applies JSON.parse to value.
4. Groups all values by key.

```
hadoopUtils.iterateKeysWithGroupedJsonValues(function(key, values) { });
```

**iterateKeysWithGroupedValues**

1. Reads input line by line. 
2. Extracts key and value from line. 
3. Groups all values by key.

```
hadoopUtils.iterateKeysWithGroupedValues(function(key, values) { });
```

### Reference for hadoop streaming utility

1. https://www.npmjs.com/package/hadoop-streaming-utils
2. https://github.com/koorchik/node-hadoop-streaming-utils
