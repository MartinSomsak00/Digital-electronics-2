# Lab 2: Martin Šomšák
Link to GitHub repository: [https://github.com/MartinSomsak00/Digital-electronics-2](https://github.com/MartinSomsak00/Digital-electronics-2)

Link to [Assignment](https://github.com/MartinSomsak00/Digital-electronics-2/blob/main/Labs/02-leds/README.md)

# Active-low and active-high LEDs

#### 1. Complete tables according to the AVR manual.

| **DDRB** | **Description** |
| :-: | :-- |
| 0 | Input pin |
| 1 | Output pin|

| **PORTB** | **Description** |
| :-: | :-- |
| 0 | Output low value |
| 1 | Output high value|

| **DDRB** | **PORTB** | **Direction** | **Internal pull-up resistor** | **Description** |
| :-: | :-: | :-: | :-: | :-- |
| 0 | 0 | input | no | Tri-state, high-impedance |
| 0 | 1 | input | yes | MCU. will source current if ext. pulled low |
| 1 | 0 | output | no | Output low (sink) |
| 1 | 1 | output | no| Output high (source) |

#### 2. Part of the C code listing with syntax highlighting, which blinks alternately with a pair of LEDs; let one LED is connected to port B and the other to port C:


```c

int main(void)
{
    // Green LED at port B
    // Set pin as output in Data Direction Register...
    DDRB = DDRB | (1<<LED_GREEN);
    // ...and turn LED off in Data Register
    PORTB = PORTB & ~(1<<LED_GREEN);

    // Configure the second LED at port C
  
    DDRC = DDRC | (1<<LED_GREEN2);

    PORTC = PORTC | (1<<LED_GREEN2);

    // Infinite loop
    while (1)
    {
        // Pause several milliseconds
        _delay_ms(BLINK_DELAY);
        PORTB = PORTB ^ (1<<LED_GREEN);
        PORTC = PORTC ^ (1<<LED_GREEN2);
    }

    // Will never reach this
    return 0;
}
}
```
### Push button

#### 1. Part of the C code listing with syntax highlighting, which toggles LEDs only if push button is pressed. Otherwise, the value of the LEDs does not change. Let the push button is connected to port D:

```c
	//push button on port D
	DDRD = DDRD & ~(1<<PUSH_BTN);
	
	PORTD = PORTD | (1<<PUSH_BTN);

	// Infinite loop
	while (1)
	{
		// Pause several milliseconds
		_delay_ms(BLINK_DELAY);
	
		if(bit_is_clear(PIND, 7))
		{
			PORTB = PORTB ^ (1<<LED_GREEN);
			PORTC = PORTC ^ (1<<LED_GREEN2);
		}
	}

    // Will never reach this
    return 0;
}
```

### Knight Rider :
![Knight Rider](pictures/1.PNG) 