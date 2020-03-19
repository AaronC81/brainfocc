# Brainfocc

Brainfocc is a **Brainfuck dialect with Occam-style concurrency**.

On top of the standard Brainfuck instructions, it has: 

  - `^` **fork**: Creates a new interpreter with an identical state to the
    current one, except for the current data byte. The data byte is set to 0 on
    the original thread, and a new unique PID on the forked thread.

  - `&` **channel select**: Chooses a channel to send and receives messages to.
    The new channel number is set with the current data byte.

  - `!` **send**: Sends a data byte to the currently selected channel, blocking
    until it's received.

  - `?` **receive**: Receives a data byte on the currently selected channel,
    blocking if one is not immediately available.

## Usage

You'll need `concurrent-ruby` and `concurrent-ruby-edge`. Invoke this like:

```
brainfocc <file>
```

## Quirks

  - The fact this exists is enough of a quirk, to be honest
  - The main executable will never terminate without a Ctrl+C