# introduction-to-javascript
William
Dan
James

Ved
David
Louis


Objects
SemiColons
Statements
Expression
loops 
functions
Object literal
For in
arrays

##Coursework 1

###Intro to Node.js

```javascript
process.argv.forEach(function (val, index, array) {
    console.log(index + ': ' + val);
});
```

##Coursework 2

###HTTP Server in Node.js

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

###DOM manipulation

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

##Coursework 4

###Regular expressions and Ajax

```javascript
var http = require('http');
var fs = require('fs');

http.createServer(function (req, res) {
var filename, index;

filename = /^\/(.*)/g.exec(req.url);

if(filename.length) {
  try {
    index = fs.readFileSync('./' + filename[0]);
    res.writeHead(200, {'Content-Type': 'text/html'});
  } catch (e) { 
    index = e.message;
  }
}

res.end(index);
```

```html
<!DOCTYPE html>
<html>

<head>
</head>

<body>
    <h1>Hello world</h1>
    <h2>Response:</h2>
    <div id="response"></div>
    <script src='https://code.jquery.com/jquery-2.1.3.js'></script>
    <script>
    $.ajax({
            url: "http://localhost:1111",
            beforeSend: function(xhr) {
                xhr.overrideMimeType("text/plain; charset=x-user-defined");
            }
        })
        .done(function(data) {
        	$('#response').text(data);
        });
    </script>
</body>

</html>
```
##Coursework 5

###Inter-page communication

```html
<!DOCTYPE html>
<html>
<head></head>
<body>
  <a id="foo" href>Click me!</a>

  <script>
    document.getElementById('foo').onclick = onFooClick;

    function onFooClick(e) {
      var scriptToInject, popUp, node, importedNode;

      scriptToInject = 'document.body.innerHTML = "Hello from the injected script!";';
      popUp = window.open('about:blank');
      node = document.createElement('script');
      node.textContent = scriptToInject;
      importedNode = popUp.document.importNode(node, true);
      popUp.document.body.appendChild(importedNode);
    }
  </script>
</body>
</html>
```

##Coursework 6

###Code golf (arrays and strings)

Write a program that takes an array of strings, selects only the strings with three characters and then returns another array containing those strings reversed.

For example:

    ['one','two','three']

...and transforms it into:

    ['eno','owt']

```javascript
['one','two','three'].filter(i => i.length == 3).map(i => i.split('').reverse().join(''))
['one','two','three'].reduce((p, i)=>i.length == 3 ? p.push(i.split('').reverse().join('')) && p : p, [])
```

##Coursework 7

Write a function that, given a string, produces a map of the indexes of all characters. For example, 
indexes("Mississippi") should return a map associating 'M' with the set {0}, 'i' with the set {1, 4, 7, 10}, and 
so on.  

```javascript
function indexes(s) {
	return s.split('').reduce(function(p, c, i) {
		if(!p[c]) { 
			p[c] = [i]; 
		} else {
			p[c].push(i);
		}
		return p;
	}, {});
}
indexes('Mississippi');
```

```scala
def index(s1: String): Map[Char, Set[Int]] = {
@tailrec def index(cache: Map[Char, Set[Int]], s2: String, pos: Int): Map[Char, Set[Int]] = {
val indexSet = cache.getOrElse(s2.head, Set[Int]()) + pos
val updatedCache = cache + (s2.head -> indexSet)
if (s2.tail.nonEmpty)
  index(updatedCache, s2.tail, pos + 1)
else
  updatedCache
}
index(Map(), s1, 0)
}
index("Mississippi").foreach { case (k, v) => println(k + " " + v) } 
```
```javascript
function indexes(s) {
	return (function go(a, i, acc) {
		if(!a.length) {
			return acc;
		}

		c = a[i];

		if(!acc[c]) {
			acc[c] = [i];
		} else {
			acc[c].push(i);
		}

		return go(a.splice(0,1) && a, i++, acc);
	}(s.split(''), 0, {}));
}
indexes('Mississippi');
```

##Coursework 8
requestanimationframe, o-auth with github, websockets, canvas, history api
