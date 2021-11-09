# Lab 7: Martin Šomšák
Link to GitHub repository: [Digital-electronics-2](https://github.com/MartinSomsak00/Digital-electronics-2)

https://github.com/MartinSomsak00/Digital-electronics-2

Link to [Assignment](https://github.com/MartinSomsak00/Digital-electronics-2/blob/main/Labs/07-uart/README.md)

https://github.com/MartinSomsak00/Digital-electronics-2/blob/main/Labs/07-uart/README.md

### Analog-to-Digital Conversion

1. Complete table with voltage divider, calculated, and measured ADC values for all five push buttons.

   | **Push button** | **PC0[A0] voltage** | **ADC value (calculated)** | **ADC value (measured)** |
   | :-: | :-: | :-: | :-: |
   | Right  | 0&nbsp;V | 0 | - |
   | Up     | 0.495&nbsp;V | 101 | - |
   | Down   | 1.203&nbsp;V | 246 | - |
   | Left   | 1.970&nbsp;V | 403 | - |
   | Select | 3.182&nbsp;V | 651 | - |
   | none   | 5&nbsp;V | 1023 | - |
   
2. Code listing of ACD interrupt service routine for sending data to the LCD/UART and identification of the pressed button. Always use syntax highlighting and meaningful comments:

```c
ISR(ADC_vect)
{
    uint16_t value = 0;
    char lcd_string[4] = "0000";
    value = ADC;                  // Copy ADC result to 16-bit variable
    
    // Clear display 
    lcd_gotoxy(8, 0);
    lcd_puts("    ");
	
	
    itoa(value, lcd_string, 10);  // Convert decimal value to string
    lcd_gotoxy(8, 0);
    lcd_puts(lcd_string);
    
    // UART
    uart_puts("\033[4;32m");
    uart_puts(" value: ");
    uart_puts(lcd_string);
    uart_puts(" ");
    
    // Clear display and display hexa value
    lcd_gotoxy(13, 0);
    lcd_puts("    ");
    itoa(value, lcd_string, 16);  // Convert decimal value to string
    lcd_gotoxy(13, 0);
    lcd_puts(lcd_string);
    
    // hexa string 
    uart_puts(lcd_string);
    uart_puts("\r\n   key: "); // newline
    
    // clear key display
    lcd_gotoxy(8, 1);
    lcd_puts("      ");
    
    // Display key on LCD and serial 
    lcd_gotoxy(8, 1);
    if (value < 75) {
        lcd_puts("Right");
        uart_puts("Right");
    } else if (value < 150) {
        lcd_puts("Up");
        uart_puts("Up");
    } else if (value < 350) {
        lcd_puts("Down");
        uart_puts("Down");
    } else if (value < 550) {
        lcd_puts("Left");
        uart_puts("Left");
    } else if (value < 800) {
        lcd_puts("Select");
        uart_puts("Select");
    } else {
        lcd_puts("None");
        uart_puts("None");
    }
    
    // UART 2xnewlines
    uart_puts("\r\n\r\n");
}
```

### UART communication

1. (Hand-drawn) picture of UART signal when transmitting three character data `De2` in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800&nbsp;Bd).

  ![](pictures/1.PNG)

2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

 ![](pictures/2.PNG)

### Temperature meter

Consider an application for temperature measurement and display. Use temperature sensor [TC1046](http://ww1.microchip.com/downloads/en/DeviceDoc/21496C.pdf), LCD, one LED and a push button. After pressing the button, the temperature is measured, its value is displayed on the LCD and data is sent to the UART. When the temperature is too high, the LED will start blinking.

1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.

   ![your figure]()