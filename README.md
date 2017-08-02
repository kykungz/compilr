# compilr
> Docker-based compiler API server

Compilr is a docker-based API server for compile and running source code.
Once you have downloaded and created a docker container using our provided image, your API server will start running automatically.

## Usage
### Request
Compilr will create a simple API server on port 8080 by default. You can compile and run your code by sending a HTTP `POST` request to your https://localhost:8080/compile route, with a JSON request body similar to:
```javascript
// This is an example of compilr-javascript

// { "content": <code> }
{ "content": "let x = 10; console.log('hello world!' + x);" }
```
**Note that each compilr may have a different request body structure, depending on the language's specification.**

For example, in Java, you must specify the file name which will be the same as your class name.
```javascript
// compilr-java

 { "files": [
    {
      "name": <class_name>,
      "content": <source_code>
    },
    {
      "name": <class_name>,
      "content": <source_code>
    }
 ] }
```
**vs**
```javascript
 // compilr-javascript

 { "files": [
   { "content": <code> },
   { "content": <code> }
 ] }
```
### Response
The response will be in JSON format with structure:
```javascript
  {
    "success": <boolean>,
    "output": <runnig_result>
  }
```
*Example:*
```javascript
  {
    "success": true,
    "output": "hello world!10\n"
  }
```
If there is a compile/run error, success field will be `false` and the error output will be shown.

---
***every compilr also provide a simple code editor frontend on your https://localhost:8080***

![frontend image](compilr.png)

# Available compilr
| Language     | URL     |
| :------------- | :------------- |
| C       | ~~[compilr-clang](https://github.com/kykungz/compilr-clang)~~ *WIP|
| Javascript       | [compilr-javascript](https://github.com/kykungz/compilr-javascript)|
| Java       |[compilr-java](https://github.com/kykungz/compilr-java)|
| Python       | ~~[compilr-python](https://github.com/kykungz/compilr-python)~~ *WIP|
