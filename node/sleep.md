# How to make a sleep function

Occasionally you'd like to put execution in pause. In other languages, this is done with a function called `sleep()`. In javascript, you might think that this can be done with `setTimeout()`, but you'd be wrong. This will only queue a task to be executed later while the main script still continues executing to completion.

It is possible to promisify the setTimout in a way to make it act like a sleep function but that isn't easy. (of course once its done you've got a function you can copy and paste easily).

Natively in js  however, theres a really cool thing called `atomics.wait()` which can be used to implement a sleep function.

```ts
function sleep(ms:number){
  Atomics.wait(new Int32Array(new SharedArrayBuffer(4)),0 ,0, ms)
}
```

How this works is that the `wait()` function is checking that the sharedarray contains a value and if so waits for a specified duration.
