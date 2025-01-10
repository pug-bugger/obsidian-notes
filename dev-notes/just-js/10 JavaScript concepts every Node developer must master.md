[[javascript]]
Link to post: https://dev.to/usman_awan/10-javascript-concepts-every-node-developer-must-master-2na

**1. JavaScript closures**
A closure in JavaScript is an inner function that has access to its outer function’s scope, even after the outer function has returned control. A closure makes the variables of the inner function private.
```
let count = (function () {
	var _counter = 0;
	return function () { return _counter += 1 }
})();

count();
count();
count();
// the counter is now 3
```
