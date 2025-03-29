# SI7021 Arduino Example (No External Library)

This Arduino sketch demonstrates how to read **humidity**, **temperature**, and calculate **dew point** using the **Si7021** sensor over I2C — with no external libraries required.

## 📦 What's Included

- `SI7021_no_lib.ino`: Sketch that communicates directly with the Si7021 sensor over I2C
- MIT License

## 🔧 Hardware Required

- Arduino board (Uno, Nano, etc.)
- Si7021 sensor module (I2C interface)
- Jumper wires

## 🔌 Wiring

| Si7021 Pin | Connect to Arduino |
|------------|--------------------|
| VDD        | 3.3V or 5V         |
| GND        | GND                |
| SDA        | A4 (Uno/Nano)      |
| SCL        | A5 (Uno/Nano)      |

> ✅ The Si7021 supports both 3.3V and 5V logic, so it's safe to use with most Arduino boards without level shifters.

## 🧠 How It Works

- Sends the `0xF5` command to measure humidity
- Sends the `0xF3` command to measure temperature
- Converts the raw I2C response to physical values (°C, % RH)
- Calculates dew point using the approximation: dewPoint = temperature - ((100 - humidity) / 5)
- Outputs results over serial

### Example Serial Output

Humidity : 43.27 % RH Celsius : 22.54 C Dew Point: 10.20 C

## 🧪 Notes

- No libraries like `Adafruit_Si7021` are used — everything runs over `Wire.h`
- If humidity reads over 100%, consider adding a `constrain(humidity, 0.0, 100.0)` in code

## 📜 License

MIT License – see `LICENSE` for details.
