# introduction-to-javascript

##Coursework 1

```javascript
process.argv.forEach(function (val, index, array) {
    console.log(index + ': ' + val);
});
```

##Coursework 2

```javascript
var http = require('http');
var fs = require('fs');

var index = fs.readFileSync('index.html');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end(index);
}).listen(9615);
```

##Coursework 3

```html
<!DOCTYPE html>
<html>
<head>
	<style>
  @-webkit-keyframes example {
    0%   {background-color: red; left:0px; top:0px;}
    25%  {background-color: yellow; left:200px; top:0px;}
    50%  {background-color: blue; left:200px; top:200px;}
    75%  {background-color: green; left:0px; top:200px;}
    100% {background-color: red; left:0px; top:0px;} 
      }
	</style>
</head>
<body>
<div id='foo'>In my craft and sullen art something in the still night.</div>	

<script>
	document.getElementById('foo').style.WebkitAnimation = "example 5s linear 2s infinite alternate";
	// document.body.innerHTML = 'foo';

</script>
</body>
</html>
```
