## Flashing an LED

With the help of the `sleep` function and a little loop, you can make the LED flash.

+ Edit the `examples/flash.rs` file in an editor with the following code:


```rust
extern crate rust_gpiozero;
use rust_gpiozero::*;
use std::thread::sleep;
use std::time::Duration;

fn main() {

// Tell the Pi which GPIO pin you are using
let mut led = LED::new(17);

loop{
    // Make the led switch on
    led.on();

    // Let the LED stay on for one second
    sleep(Duration::from_secs(1));

    // Make the led switch off
    led.off();

    // Let the LED stay off for one second
    sleep(Duration::from_secs(1));
    }
}
```
+ Run run flash example by running the following command:

```bash
cargo run --example flash
```

+ The LED should be flashing on and off. To exit the program press **Ctrl + C** on your keyboard.

+ In `rust_gpiozero`, an `LED` has a `blink` method which allows you to simplify the above code. The method takes two parameters, `on_time` and `off_time`.
`on_time` is the number of second(s) the `LED` should stay on and `off_time` is the number of second(s) that the `LED` should stay off.

+ Modify your code to the following:

```rust
extern crate rust_gpiozero;
use rust_gpiozero::*;

fn main() {

    // Tell the Pi which GPIO pin you are using
    let mut led = LED::new(17);

    // let the LED blink indefinitely, staying on for 1 sec and off for 1 sec    
    led.blink(1,1);
}
```

+ Run the code. The LED should blink indefinitely, staying on for one second and off for one second. To exit the program press **Ctrl + C** on your keyboard. 

+ Try changing the parameters to blink to make it blink faster or slower.