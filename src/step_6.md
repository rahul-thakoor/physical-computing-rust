## Flashing an LED

With the help of the `sleep` function and a little loop, you can make the LED flash.

+ Create a new binary executable project( called `flash` here).


+ Edit the `examples/flash.rs` file in an editor with the following code:


```rust
extern crate rust_gpiozero;
use rust_gpiozero::*;
use std::thread;
use std::time::Duration;

fn main() {

// Tell the Pi which GPIO pin you are using
let mut led = LED::new(17);

loop{
    // Make the led switch on
    led.on();

    // Let the LED stay on for one second
    thread::sleep(Duration::from_secs(1));

    // Make the led switch off
    led.off();

    // Let the LED stay off for one second
    thread::sleep(Duration::from_secs(1));
    }
}
```
+ Run run flash example by running the following command:

```bash
cargo run --example flash
```

+ The LED should be flashing on and off. To exit the program press **Ctrl + C** on your keyboard.
