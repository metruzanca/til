# What executes first? The Properties or the Constructor?

In most languages its the Properties first, but with how javascript doesn't conform to normal OOP and instead uses a prototypal inheritance model I wanted to double check.

As per usual, when I test things out in js I'm either using the browser console or Quokka the Vscode extension.

I wrote this small script out which uses a generator (something I don't use much).
```js
  function* when(){
    let i = 0;
    while(true){
      yield i;
      i++;
    }
  }
  const w = when()
  const next = () => w.next().value

  class Test{
    prop = next()
    constructor(){
      this.constr = next()
    }
  }
  const t = new Test()
  console.log(t)
```
The output proves that like most other languages the props get evaluated first and the constructor second.
```
Object { prop: 0, constr: 1 }
```

