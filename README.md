# ULTRASONICO-CON-LCD

## PROGRAMACIÓN

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR   0x27
#define LCD_COLUMNS 20
#define LCD_LINES  4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

lcd.setCursor(2,0);
lcd.print("Diplomado V");
lcd.setCursor(2,1);
lcd.print("Mecatronica");
delay(2000);

lcd.clear();
lcd.setCursor(2,0);
lcd.print("Ing. Raul");
lcd.setCursor(2,1);
lcd.print("Ing. Electrico");
delay(2000);

lcd.clear();
TempAndHumidity  data = dhtSensor.getTempAndHumidity();
Serial.println("Temp: " + String(data.temperature, 1) + "°C");
Serial.println("Humidity: " + String(data.humidity, 1) + "%");
Serial.println("---");
lcd.setCursor(0, 0);
lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
lcd.setCursor(0, 1);
lcd.print("  Humidity: " + String(data.humidity, 1) + "% ");
delay(2000);
}
```

## LIBRERIAS

1. DHT sensor library for ESPx
2. LiquidCrystal I2C

## CONEXIÓN

![](https://github.com/RaulCasS/ULTRASONICO-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-12%20221837.png?raw=true)

## RESULTADOS

![](https://github.com/RaulCasS/ULTRASONICO-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-12%20222045.png?raw=true)
![](https://github.com/RaulCasS/ULTRASONICO-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-12%20222148.png?raw=true)
![](https://github.com/RaulCasS/ULTRASONICO-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-12%20222255.png?raw=true)

### CRÉDITOS

Desarrollador por el Ing. Raúl Castañeda Sotelo

https://github.com/RaulCasS (GitHub)
