# Call Stack
## When Functions Call Functions

If you start organizing your room, but then notice your closet is a mess, so you start organizing your closet, you might want to do the following three things:

1. Pause cleaning the rest of the room
2. Dive into the closet and focus your energy there
3. When you're done, hopefully remember where you were with the rest of the room.

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

Copy and paste this code somewhere like [repl.it](https://repl.it/languages/javascript).

It's the same as before, now with `console.log`'s sprinkled throughout

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

1. You don't get icecream until you're DONE cleaning your room
2. You're not done cleaning your room 'til you're done cleaning your closet
3. You're not done cleaning your closet until your shoes are in order.

