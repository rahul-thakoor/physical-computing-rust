## Switching an LED on and off

> [GPIO Zero](https://gpiozero.readthedocs.io/) is a new Python library which provides a simple interface to everyday GPIO components. It comes installed by default in Raspbian.

> [`rust_gpizero`](https://docs.rs/rust_gpiozero/0.1.0/rust_gpiozero/) is a Rust implementation of the GPIO Zero library. It provides a simple interface to GPIO devices on the Raspberry Pi and is ideal for getting started with physical computing using Rust.

+ Use `cargo` to start a project

+ You can switch an LED on and off by typing commands directly into the Python interpreter window (also known as the Python **shell**). Let's do this by first importing the GPIO Zero library. You also need to tell the Pi which GPIO pin you are using - in this case pin 17. Next to the chevrons `>>>`, type:

    ``` python
    from gpiozero import LED
    led = LED(17)
    ```

    Press **Enter** on the keyboard.

+ To make the LED switch on, type the following and press **Enter**:

    ``` rust
    extern crate rust_gpiozero;
    use rust_gpiozero::*;

    fn main() {

    // Create a new LED attached to Pin 17

    let mut led = LED::new(17);

    // blink the LED
    // on_time: 2 seconds and off_time: 3 seconds

    led.blink(2,3);

    }
    ```

+ To make it switch off you can type:

    ```python
    led.off()
    ```

+ Your LED should switch on and then off again. But that's not all you can do.
