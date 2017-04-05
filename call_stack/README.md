# Call Stack - _When Functions Call Functions_

If you start organizing your room, but then notice your closet is a mess, so you start organizing your closet, you might want to do the following three things:

1. Pause cleaning the rest of the room
2. Dive into the closet and focus your energy there
3. When you're done, hopefully remember where you were with the rest of the room so you don't _start over_

**Hooray!** You figured out the call stack.

Let's try it with functions.

```javascript
function organizeRoom(){
  // other room cleaning
  organizeCloset();
}

function organizeCloset(){
  // other closet stuff
  organizeShoes();
}

function organizeShoes(){
  console.log("Putting shoes in order");
}

organizeRoom(); // Don't forget to run your functions :D
```

Easy right? Start cleaning your room, then start cleaning the closet, then organize your shoes.

### It's not straight forward, it's nested

So you might be imagining the order of tasks like this
```
organizeRoom -> organizeCloset -> organizeShoes
```
In essence, do 'A' then do 'B' then do 'C'.

**Not quite...**

It's nested, like the russian dolls.

```
Start organizingRoom

    Start organizingCloset

      Start organizingShoes

      Finish organizingShoes

    Finish organizingCloset

Finish organizingRoom
```

### You're not done with the room until you're done with the closet

Copy and paste this code somewhere like [repl.it/languages/javascript](https://repl.it/languages/javascript).

It's the same as before, now with `console.log`'s sprinkled throughout

### Predict the order of the logs, then run it!

```javascript
function organizeRoom(){
  console.log('start cleaning room');
  organizeCloset();
  console.log('done cleaning room');
}

function organizeCloset(){
  console.log('  start cleaning closet');
  organizeShoes();
  console.log('  done cleaning closet');
}

function organizeShoes(){
  console.log('   start cleaning shoes');
  console.log("----> working on shoes");
  console.log('   done cleaning shoes');
}

organizeRoom();
console.log('Get icecream!');
```

**Does your console look like this?**

```
start cleaning room

  start cleaning closet

   start cleaning shoes

----> working on shoes

   done cleaning shoes

  done cleaning closet

done cleaning room

Get icecream!
```

1. **You don't get icecream until you're DONE cleaning your room**
2. **You're not done cleaning your room 'til you're done cleaning your closet**
3. **You're not done cleaning your closet until your shoes are in order**



### Returning back where you were without forgetting

When function `A` calls function `B`, `A` has to pause itself, then `B` runs, and whatever `B` returns, is returned back to where `A` was when it invoked it.

_i.e. If I was halway done cleaning my room when I started on the closet, I'll return back to being halfway done with the room when the closet is done._

**Look at the following code and try to answer these questions:**

  - What is the value of `n` inside `A`, inside `B` and inside `C`?
  - Which function returns first?
  - Where does it's return value go?

### Think through this code

```javascript
function A(n){
  var val = n + B(n+2);
  return val;
}

function B(n){
  var val = n + C(n+2);
  return val;
}

function C(n){
  var val = "hi!" + n;
  return val;
}

A(5);
```

Try to predict what `A(5)` returns, then once you've got your guess, run it.

### Run this code
It's the same, just with some `console.log` help to visualize each step.

```javascript
function A(n){
  console.log('start A. n =', n)
  var val = n + B(n+2);
  console.log('finish A. val =', val)
  return val;
}

function B(n){
  console.log('  start B. n =', n)
  var val = n + C(n+2);
  console.log('  finish B. val =', val)
  return val;
}

function C(n){
  console.log('    start C. n =', n)
  var val = "hi!" + n;
  console.log('    finish C. val =', val)
  return val;
}

A(5);
console.log('\nAll Done!');

```

You should see this in the console.

```
start A. n = 5

  start B. n= 7

    start C. n= 9

    finish C. val = hi!9

  finish B. val = 7hi!9

finish A. val = 57hi!9

All Done!
```