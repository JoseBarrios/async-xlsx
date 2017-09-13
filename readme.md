[async-xlsx](https://github.com/JoseBarrios/async-xlsx) 
=================

Adds [async](https://www.npmjs.org/package/each-async) support to [node-xlsx](http://mgcrea.github.com/node-xlsx).

Quick start
-----------

Parsing a xlsx from file/buffer
```javascript
var xlsx = require('async-xlsx');

//  ------------------ Synchronous ----------------------------
// Covert excel file to JSON object
var obj = xlsx.parse(__dirname + '/myFile.xlsx'); 
// Convert excel file to buffer
var buffer = xlsx.parse(fs.readFileSync(__dirname + '/myFile.xlsx')); 
// Returns a buffer
var data = [[1,2,3],[true, false, null, 'sheetjs'],['foo','bar',new Date('2014-02-19T14:30Z'), '0.3']];
var buffer = xlsx.build([{name: "mySheetName", data: data}]); 



//  ------------------ Asynchronous ----------------------------
// Transform an Excel file to JSON or an 2D array (async)
xlsx.parseFileAsyncArray(__dirname + '/myFile.xlsx', {options}, function(parsedObject){
	// Callbacks happens when the Excel data is fully loaded and ready for use	
});

// Transform an Excel file to a CSV(async)
const optionsCSV = { RS: '\n', FS: ';' };
xlsx.parseFileAsyncCSV(__dirname + '/myFile.xlsx', {options}, optionsCSV, function(csvData){
	// Callbacks happens when the Excel data is fully loaded and ready for use	
});


//  ------------------ Asynchronous ----------------------------
// Easily build an Excel document from a 2D array (async)
xlsx.buildAsync( [{name: "SheetName", data: [[2D][array]] }], {options}, function(error, xlsBuffer) {
	if(!error){
		// Buffer is ready.
	}
});

```

Building a plist from an object
```javascript
var xlsx = require('async-xlsx');

var data = [[1,2,3],[true, false, null, 'sheetjs'],['foo','bar',new Date('2014-02-19T14:30Z'), '0.3']];
var buffer = xlsx.build([{name: "mySheetName", data: data}]); // returns a buffer

```

Testing
-------

`async-xlsx` is tested with `nodeunit`.

>
	npm install --dev
	npm test

Contributing
------------

Please submit all pull requests the against master branch. If your unit test contains javascript patches or features, you should include relevant unit tests. Thanks!

Authors
-------
[Jose Barrios] (https://github.com/JoseBarrios)


License
---------------------

     Licensed under the Apache License, Version 2.0 (the "License");
     you may not use this file except in compliance with the License.
     You may obtain a copy of the License at

         http://www.apache.org/licenses/LICENSE-2.0

     Unless required by applicable law or agreed to in writing, software
     distributed under the License is distributed on an "AS IS" BASIS,
     WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
     See the License for the specific language governing permissions and
     limitations under the License.

  Except where noted, this license applies to any and all software programs and associated documentation files created by the Original Author and distributed with the Software:

  'async-xlsx' is a modified version of SheetJS gist examples, Copyright (c) SheetJS.
