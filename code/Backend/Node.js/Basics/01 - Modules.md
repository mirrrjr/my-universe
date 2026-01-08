## Node.js Built-in Modules

Node.js has a set of built-in modules which you can use without any further installation.

Here is a list of the built-in modules of Node.js version 6.10.3:

| Module                                                                    | Description                                                |
| ------------------------------------------------------------------------- | ---------------------------------------------------------- |
| [assert](https://www.w3schools.com/nodejs/ref_assert.asp)                 | Provides a set of assertion tests                          |
| [buffer](https://www.w3schools.com/nodejs/ref_buffer.asp)                 | To handle binary data                                      |
| child_process                                                             | To run a child process                                     |
| [cluster](https://www.w3schools.com/nodejs/ref_cluster.asp)               | To split a single Node process into multiple processes     |
| [crypto](https://www.w3schools.com/nodejs/ref_crypto.asp)                 | To handle OpenSSL cryptographic functions                  |
| [dgram](https://www.w3schools.com/nodejs/ref_dgram.asp)                   | Provides implementation of UDP datagram sockets            |
| [dns](https://www.w3schools.com/nodejs/ref_dns.asp)                       | To do DNS lookups and name resolution functions            |
| domain                                                                    | Deprecated. To handle unhandled errors                     |
| [events](https://www.w3schools.com/nodejs/ref_events.asp)                 | To handle events                                           |
| [fs](https://www.w3schools.com/nodejs/ref_fs.asp)                         | To handle the file system                                  |
| [http](https://www.w3schools.com/nodejs/ref_http.asp)                     | To make Node.js act as an HTTP server                      |
| [https](https://www.w3schools.com/nodejs/ref_https.asp)                   | To make Node.js act as an HTTPS server.                    |
| [net](https://www.w3schools.com/nodejs/ref_net.asp)                       | To create servers and clients                              |
| [os](https://www.w3schools.com/nodejs/ref_os.asp)                         | Provides information about the operation system            |
| [path](https://www.w3schools.com/nodejs/ref_path.asp)                     | To handle file paths                                       |
| punycode                                                                  | Deprecated. A character encoding scheme                    |
| [querystring](https://www.w3schools.com/nodejs/ref_querystring.asp)       | To handle URL query strings                                |
| [readline](https://www.w3schools.com/nodejs/ref_readline.asp)             | To handle readable streams one line at the time            |
| [stream](https://www.w3schools.com/nodejs/ref_stream.asp)                 | To handle streaming data                                   |
| [string_decoder](https://www.w3schools.com/nodejs/ref_string_decoder.asp) | To decode buffer objects into strings                      |
| [timers](https://www.w3schools.com/nodejs/ref_timers.asp)                 | To execute a function after a given number of milliseconds |
| [tls](https://www.w3schools.com/nodejs/ref_tls.asp)                       | To implement TLS and SSL protocols                         |
| tty                                                                       | Provides classes used by a text terminal                   |
| [url](https://www.w3schools.com/nodejs/ref_url.asp)                       | To parse URL strings                                       |
| [util](https://www.w3schools.com/nodejs/ref_util.asp)                     | To access utility functions                                |
| v8                                                                        | To access information about V8 (the JavaScript engine)     |
| [vm](https://www.w3schools.com/nodejs/ref_vm.asp)                         | To compile JavaScript code in a virtual machine            |
| [zlib](https://www.w3schools.com/nodejs/ref_zlib.asp)                     | To compress or decompress files                            |

### HTTP module
Node.js has a built-in module called HTTP, which allows Node.js to transfer data over the Hyper Text Transfer Protocol (HTTP).

To include the HTTP module, use the `require()` method

>Read the Query String

```javascript
const http = require('http');  

http.createServer(function (req, res) {  
  res.writeHead(200, {'Content-Type': 'text/html'});  
  res.write(req.url);  
  res.end();  
}).listen(8080);
```

>Split the Query String

```javascript
const http = require('http');  
const url = require('url');  

http.createServer(function (req, res) {  
  res.writeHead(200, {'Content-Type': 'text/html'});  
  let q = url.parse(req.url, true).query;
  let txt = q.year + " " + q.month;  
  res.end(txt);  
}).listen(8080);
```

### FS module | Node.js as a File Server

The Node.js file system module allows you to work with the file system on your computer.

To include the File System module, use the `require()` method:
>`fs = require('fs');`

Common use for the File System module:
- Read files
- Create files
- Update files
- Delete files
- Rename files

>Read file

```javascript
const http = require('http');  
const fs = require('fs');  

http.createServer(function (req, res) {  
  fs.readFile('index.html', function(err, data) {
	res.writeHead(200, {'Content-Type': 'text/html'});  
	res.write(data);  
    return res.end();  
  });  
}).listen(8080);
```

>Create file

The File System module has methods for creating new files:

- `fs.appendFile()`
- `fs.open()`
- `fs.writeFile()`

The `fs.appendFile()` method appends specified content to a file. If the file does not exist, the file will be created:
```javascript
const fs = require('fs');  
  
fs.appendFile('mynewfile1.txt', 'Hello content!', function (err) {  
  if (err) throw err;  
  console.log('Saved!');  
});
```


The `fs.open()` method takes a "flag" as the second argument, if the flag is "w" for "writing", the specified file is opened for writing. If the file does not exist, an empty file is created:
```javascript
const fs = require('fs');  
  
fs.open('mynewfile2.txt', 'w', function (err, file) {  
  if (err) throw err;  
  console.log('Saved!');  
});
```

The `fs.writeFile()` method replaces the specified file and content if it exists. If the file does not exist, a new file, containing the specified content, will be created:
```javascript
const fs = require('fs');  
  
fs.writeFile('mynewfile3.txt', 'Hello content!', function (err) {  
  if (err) throw err;  
  console.log('Saved!');  
});
```

>Update file

The File System module has methods for updating files:

- `fs.appendFile()`
- `fs.writeFile()`

The `fs.appendFile()` method appends the specified content at the end of the specified file
The `fs.writeFile()` method replaces the specified file and content

>Delete file

To delete a file with the File System module,  use the `fs.unlink()` method.

The `fs.unlink()` method deletes the specified file:

```javascript
const fs = require('fs');  
  
fs.unlink('mynewfile2.txt', function (err) {  
  if (err) throw err;  
  console.log('File deleted!');  
});
```

>Rename file

To rename a file with the File System module,  use the `fs.rename()` method.

The `fs.rename()` method renames the specified file:
```javascript
const fs = require('fs');  
  
fs.rename('mynewfile1.txt', 'myrenamedfile.txt', function (err) {  
  if (err) throw err;  
  console.log('File Renamed!');  
});
```

>Upload file

There is a very good module for working with file uploads, called "Formidable".

The Formidable module can be downloaded and installed using NPM:
```javascript
const http = require('http');  
const formidable = require('formidable');  

http.createServer(function (req, res) {  
  if (req.url == '/fileupload') {  
    var form = new formidable.IncomingForm();  
    form.parse(req, function (err, fields, files) {  
      res.write('File uploaded');  
      res.end();  
    });
  } else {  
    res.writeHead(200, {'Content-Type': 'text/html'});  
    res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');  
    res.write('<input type="file" name="filetoupload"><br>');  
    res.write('<input type="submit">');  
    res.write('</form>');  
    return res.end();  
  }  
}).listen(8080);
```


---
### URL Module
The URL module splits up a web address into readable parts.
```javascript
var url = require('url');  
var adr = 'http://localhost:8080/default.htm?year=2017&month=february';  
var q = url.parse(adr, true);  
  
console.log(q.host); //returns 'localhost:8080'  
console.log(q.pathname); //returns '/default.htm'  
console.log(q.search); //returns '?year=2017&month=february'  

var qdata = q.query; //returns an object: { year: 2017, month: 'february' }  
console.log(qdata.month); //returns 'february'
```

Example:
```javascript
var http = require('http');  
var url = require('url');  
var fs = require('fs');  
  
http.createServer(function (req, res) {  
  var q = url.parse(req.url, true);  
  var filename = "." + q.pathname;  
  fs.readFile(filename, function(err, data) {  
    if (err) {  
      res.writeHead(404, {'Content-Type': 'text/html'});  
      return res.end("404 Not Found");  
    }   
    res.writeHead(200, {'Content-Type': 'text/html'});  
    res.write(data);  
    return res.end();  
  });  
}).listen(8080);
```

## Custom modules

You can create your own modules, and easily include them in your applications.

The following example creates a module that returns a date and time object:

```javascript
// myModule.js
exports.myDateTime = () => {
	return Date();
}

// server.js
const http = require('http);
const dt = require('./myModule.js');

http.createServer((req, res) => {  
  res.writeHead(200, {'Content-Type': 'text/html'});  
  res.write("The date and time are currently: " + **dt.myDateTime()**);  
  res.end();  
}).listen(8080, () => console.log("Server running on 8080"));
```

