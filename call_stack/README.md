# Call Stack
## When Functions Call Functions

If you start organizing your room, but then notice your closet is a mess, so you start organizing your closet, you might want to do the following three things:

1. Pause cleaning the rest of the room
2. Dive into the closet and focus your energy there
3. When you're done, hopefully remember where you were with the rest of the room.

**Hooray!** You figured out the call stack.

Let's try it with functions.

```javascript
var organizeRoom = function(n){
  organizeCloset();
}

var organizeCloset = function(n){
  organizeShoes();
}

var organizeShoes = function(n){
  console.log("Putting shoes in order");
}

organizeRoom(); // Don't forget to run your functions :D
```


