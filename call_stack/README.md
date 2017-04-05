# Call Stack
## When Functions Call Functions

If you mean to organize your room, but once you get started, you realize you need to organize your closet you have to do three things:

1. Pause cleaning the rest of the room
2. Dive into the closet and focuse your energy there
3. When you're done, hopefully remember where you were with the rest of the room.

Hooray! You figured out the call stack.

Let's try it with functions.

```javascript
var organizeRoom = function(n){
  return 1 + b(n+2);
}

var organizeCloset = function(n){
  return = 2 + c(n+2);
}

var organizeShoes = function(n){
  return = "hi!" + n;
}

organizeRoom(); //Call it!
```


