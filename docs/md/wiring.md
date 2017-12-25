# Wiring

## Wiring Power circuit
Based on Adafruit pigrrl zero: https://learn.adafruit.com/pigrrl-zero/software?view=all#power    
![Power](img/03_Power.jpg)

## Wiring Buttons
### Stripboard 
![Stripboard](img/04_Buttons_stripboard.jpg)
### Raspberry Pi
![Rpi_Buttons](img/05_Buttons_RPI.jpg)

| IN/OUT | TOP/BOTTOM | POSITION  | COLOR  | GPIO | NAME             |
|--------|------------|-----------|--------|------|------------------|
| IN     | BOT        | 1         | BLACK  | GND  | GROUND (Pad)     |
| OUT    | BOT        | 4         | BLACK  | GND  | GROUND (Buttons) |
| IN     | TOP        | 4         | BLUE   | 4    | LEFT             |
| IN     | BOT        | 4         | PURPLE | 13   | RIGHT            |
| OUT    | BOT        | 3         | ORANGE | 16   | UP               |
| IN     | BOT        | 2         | BROWN  | 26   | DOWN             |
| IN     | BOT        | 5         | RED    | 6    | A                |
| IN     | TOP        | 7         | YELLOW | 27   | B                |
| OUT    | BOT        | 2         | BLUE   | 20   | Y                |
| IN     | TOP        | 6         | GREEN  | 17   | X                |
| OUT    | BOT        | 5         | YELLOW | 12   | LEFT TRIGGER     |
| IN     | BOT        | 7         | GREEN  |  1   | RIGHT TRIGGER    |

## Wiring MPU9250 (Optional)
![MPU](img/06_Screen_MPU9250.jpg)