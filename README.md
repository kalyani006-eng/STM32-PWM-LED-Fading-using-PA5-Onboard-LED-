# 🌟 STM32 PWM LED Fading using PA5 (Onboard LED)

This STM32 project demonstrates how to fade the **onboard LED (PA5)** using **PWM (Pulse Width Modulation)** via **TIM1**. The brightness increases and decreases in a loop, producing a smooth visual fading effect.

## 🚀 Features

- PWM control using TIM1
- LED brightness fade-in and fade-out loop
- Runs on STM32F103C8T6 (Blue Pill)
- Uses HAL drivers and STM32CubeIDE

## 🔧 Hardware Setup

| Pin   | Function        |
|-------|-----------------|
| PA5   | Onboard LED (LD2) |
| GND   | Common Ground    |

No external components required if using onboard LED.

## ⚙️ Configuration

- **PWM Timer:** TIM1
- **PWM Channel:** CH1
- **Output Pin:** PA5
- **PWM Resolution:** 8-bit (0–255)
- **Fade Delay:** 50ms step delay

## 🧪 How It Works

The duty cycle of TIM1's PWM output is gradually increased from `0 → 255` (LED fades in), then decreased `255 → 0` (LED fades out). This produces a breathing/fading LED effect.

## 🧰 Tools Used

- 🧠 STM32CubeIDE
- ⚙️ STM32 HAL Library
- 🐞 ST-LINK debugger
- 🧪 Putty (optional for UART output)

## 🖥️ Sample Code Snippet

```c
for (int i = 0; i < 255; i++) {
    __HAL_TIM_SET_COMPARE(&htim1, TIM_CHANNEL_1, i);
    HAL_Delay(50);
}
for (int i = 255; i > 0; i--) {
    __HAL_TIM_SET_COMPARE(&htim1, TIM_CHANNEL_1, i);
    HAL_Delay(50);
}
