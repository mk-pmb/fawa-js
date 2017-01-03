
<!--#echo json="package.json" key="name" underline="=" -->
fawa
====
<!--/#echo -->

<!--#echo json="package.json" key="description" cut-tail=":" -->
FaWA = Functions as Web Apps
<!--/#echo -->


What?
-----

__Conceptually:__
Use plain old functions as web apps (like ["web"][npm-web]), and on top,
reunite the request/response pair.
Compose and transform your web app's I/O from the inside as easily
as it is to compose and transform your web apps from the outside.


__In this package:__
Adapters that translate between ["connect"][npm-connect] style and FaWA style.


Why?
----

The web approach makes it very easy to compose web apps in
plain JavaScript, because in "web", each web app is just a function.
No need for a middleware API, just use your regular function composition.
It also simplifies the response API by using just one respond function
instead of a full-featured stream interface, so you can intercept and
modify a web app's result with regular function composition, and save
a great deal of stream headaches.

Nonetheless, "web" retains the customary dichotomy of request and response.

This hit me when I tried to write a compatibility adapter that would make
my web app work in both the "web" and "connect" framework.
I couldn't just wrap my function in another one, because I wanted to use
properties of that function for my API, so I had to make the adapter work
inside my app function.
Since my adapter function is, obviously, a function, it can return only one
value. I'd always have to unpack either request or response from the other,
or unpack both from some container.
No amount of destructuring syntax could hide the fact that these two
belong together.



Usage
-----
see [doc/demo/usage.js](doc/demo/usage.js)
:TODO:

<!--!#include file="test/usage.js" start="  //#u" stop="  //#r"
  outdent="  " code="javascript" -->
```javascript
var fawa = require('fawa');
D.result  = fawa(null);
D.expect('===',           null);
```
<!--/include-->

```bash
$ fawa foo
bar
```


<!--#toc stop="scan" -->


Mischelaneous
-------------

  * Pronunciation: I suggest German, both "a" like the one in "father".




  [npm-web]: https://www.npmjs.com/package/web
  [npm-web6]: https://www.npmjs.com/package/web6
  [npm-connect]: https://www.npmjs.com/package/connect


License
-------
<!--#echo json="package.json" key=".license" -->
ISC
<!--/#echo -->
