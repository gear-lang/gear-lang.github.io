# Introduction to Gear

## Naming Conventions

In Gear the way you name your identifiers is important.

### const Correctness

All messages which mutate state on an object should end with a `!` character.

If an object is delcared `const`, then it is a compile time error if it's sent a mutating message.

If you declare an object with the `const` qualifier and you send it a message ending with `!`, then a compiler error will occur.  This is because you've declared an immutable object, but `!` indicates the object is being mutated.  This feature is strictly compile time only and can be disabled.

The standard library follows this convention and you are encouraged to do so as well.

There are three ways to disable this feature:

1. Command line (see the `--const-correctness` flag for `gear.exe`)
2. C API
3. Inline compiler directive

Here are some situtations where you might want to disable const correctness:

1. The object or application as a whole is state heavy.
2. You have a method which mutates internal state, but from the consumers perspective is immutable (example: dynamic programming).
