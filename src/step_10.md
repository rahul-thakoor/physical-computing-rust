## Using a buzzer

There are two main types of buzzer: *active* and *passive*.

A *passive* buzzer emits a tone when a voltage is applied across it. It also requires a specific signal to generate a variety of tones. The *active* buzzers are a lot simpler to use, so these are covered here.

### Connecting a buzzer

An *active* buzzer can be connected just like an LED, but as they are a little more robust, you won't be needing a resistor to protect them.

Set up the circuit as shown below:

![buzzer](images/buzzer-circuit.png)

+ Modify the `examples/buzzer.rs` file:

    ```rust
    extern crate rust_gpiozero;
    use rust_gpiozero::*;
    use std::thread::sleep;
    use std::time::Duration;

    fn main() {

    // Tell the Pi which GPIO pin you are using
    let mut buzzer = Buzzer::new(17);    

    }
    ```


+ In `rust_gpiozero`, a `Buzzer` works exactly like an `LED`, so try adding a `buzzer.on();` and `buzzer.off();` into your loop:

    ```rust
    loop{
        // Make the buzzer switch on
        buzzer.on();

        // Wait for one second
        sleep(Duration::from_secs(1));

        // Make the buzzer switch off
        buzzer.off();

        // Wait for one second
        sleep(Duration::from_secs(1));
        }

    ```

+ A `Buzzer` has a `beep(on_time,off_time)` method which works like an `LED`'s `blink`. Try it out:

    ```rust
        // Let the buzzer beep
        buzzer.beep(1,1);
    
    ```
