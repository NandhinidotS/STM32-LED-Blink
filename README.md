# STM32 NUCLEO-F446RE LED Blink

## Project Overview

This project blinks the on-board green user LED (**LD2**) of the **STM32 NUCLEO-F446RE** board using the STM32 HAL library.

The LED stays **ON for 1 second** and **OFF for 1 second**, so one full blink cycle takes **2 seconds**.

The project was created with **STM32CubeMX** and built, flashed and run with **STM32CubeIDE 2.2.0**.

## Key Features

- STM32 NUCLEO-F446RE board
- On-board LED (LD2) control
- GPIO output configuration using STM32CubeMX
- STM32 HAL library
- Toggle-based LED blinking
- 1 second delay using HAL_Delay()
- Programming and debugging through the on-board ST-LINK

## Hardware Required

| Component | Quantity |
| --------- | -------- |
| STM32 NUCLEO-F446RE board | 1 |
| USB cable (data cable) | 1 |

No external components are needed. The LED is on the board.

## System Architecture

```
STM32F4 Microcontroller
          ↓
   GPIO Pin PA5
          ↓
 On-board LED (LD2)
```

## Pin Configuration

| Signal | MCU Pin | Mode |
| ------ | ------- | ---- |
| LD2 (green user LED) | PA5 | GPIO_Output |

## STM32CubeMX Configuration

1. Create a new project and select the **NUCLEO-F446RE** board in the Board Selector.
2. Initialize all peripherals with their default mode.
3. Check that **PA5** is set as `GPIO_Output` and labeled `LD2`.
4. In Project Manager, set the toolchain to **STM32CubeIDE**.
5. Click **Generate Code**.

## Code

The code is added inside the main loop in `Core/Src/main.c`:

```c
/* USER CODE BEGIN 3 */
HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);
HAL_Delay(1000);
/* USER CODE END 3 */
```

## Working

`HAL_GPIO_TogglePin()` changes the state of the LED pin each time it runs.

`HAL_Delay(1000)` waits 1000 ms before the next toggle.

```
LED ON  → wait 1 s → LED OFF → wait 1 s → repeat
```

## Output

The green LED (LD2) on the board blinks continuously with a 2 second cycle.

### LED Blink Output

![LED Blink Output](Output.jpeg)

## How to Run

1. Open **STM32CubeIDE**.
2. Go to `File → Import → General → Existing Projects into Workspace`.
3. Select the project folder and click **Finish**.
4. Build the project with the hammer icon.
5. Connect the board with a USB cable.
6. Click **Run** and accept the default debug configuration.

## Testing

| Test | Result |
| ---- | ------ |
| Build | 0 errors, 0 warnings |
| Flash through ST-LINK | Successful |
| LD2 blinking | Every 1 second ON / 1 second OFF |

## Important Notes

### Jumpers

Both **CN2** jumper caps on the board must be fitted. If they are missing, the programmer cannot connect to the chip and the debugger shows:

```
Error in initializing ST-LINK device.
Reason: No device found on target.
```

### Code Placement

Write your own code only between the `USER CODE BEGIN` and `USER CODE END` comments. Anything outside them is erased when the code is regenerated in CubeMX.

### USB Cable

Use a data-capable USB cable. Some cables only charge.

## Technologies and Concepts

- STM32 NUCLEO-F446RE
- STM32CubeIDE 2.2.0
- STM32CubeMX
- STM32 HAL library
- GPIO output
- HAL_GPIO_TogglePin
- HAL_Delay
- ST-LINK programming and debugging

## Future Improvements

- Two external LEDs blinking alternately
- Push button controlled LEDs
- Ultrasonic sensor distance measurement
- 16×2 I2C LCD display
- UART serial output
- Timer-based blinking without HAL_Delay

# 🎥 Project Video

[▶️ Watch the LED Blink Demonstration](https://drive.google.com/file/d/1-alz60q_yz7m7Dc0q-guLLVWQuhK1pGI/view?usp=drivesdk)