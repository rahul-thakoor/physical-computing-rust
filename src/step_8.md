## Manually controlling the LED

You can now combine your two programs written so far to control the LED using the button.

+ Edit the `examples/led_button.rs` file to add the following code:

```rust
extern crate rust_gpiozero;
use rust_gpiozero::*;
use std::thread::sleep;
use std::time::Duration;

fn main() {

// Tell the Pi which GPIO pin you are using
let mut led = LED::new(17);

// Create a button which is attached to Pin 22
let button = Button::new(22);


button.wait_for_press();
led.on();
sleep(Duration::from_secs(3));
led.off();

}

```

+ Save and run your program. When you push the button the LED should come on for three seconds.
