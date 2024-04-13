# じこいち君 プログラムテンプレート

## 利用する前に
使われているマイコンのXIAOに書き込むために以下のリンクよりセットアップしてください。

[xiao-rp2040](https://wiki.seeedstudio.com/XIAO-RP2040-with-Arduino/)

## 使用上の注意

.inoファイル名とリポジトリ名は揃えること。


## Example

以下は全てmain.inoに記載する。

前方移動
```C++
#include "zikoichi_kun_api.hpp"

void setup() {
  zk_api::setup();
}

void loop() {
  zk_api::xyz_control(1.0, 0.0, 0.0, 50);
}

```


## zk_api

### namespace
```C++
namespace zk_api
```

### xyz_control

水平方向をxy、回転をzで表し単位ベクトルで入力する。powerでモータ出力を決定する。

```C++
inline void xyz_control(float x, float y, float z, float power)
```

| 変数名 | 型 | 想定される範囲 |
|:-----------|------------:|:------------:|
| x       | float        | -1.0 ~ 1.0         |
| y       | float        | -1.0 ~ 1.0         |
| z       | float        | -1.0 ~ 1.0         |
| power   | float        | -255.0 ~ 255.0     |

### control

特定のモータの回転速度を決める

```C++
inline void control_front_right(int power)
```
```C++
inline void control_front_left(int power)
```
```C++
inline void control_rear_left(int power)
```
```C++
inline void control_rear_right(int power)
```

| 変数名 | 型 | 想定される範囲 |
|:-----------|------------:|:------------:|
| power   | int        | -255 ~ 255    |


### PWM

特定のモータのPWM dutyを決める

```C++
inline void front_right_pwm(int value)
```
```C++
inline void front_left_pwm(int value)
```
```C++
inline void rear_left_pwm(int value)
```
```C++
inline void rear_right_pwm(int value)
```

| 変数名 | 型 | 想定される範囲 |
|:-----------|------------:|:------------:|
| value   | int        | 0 ~ 255    |

### CW/CCW

特定のモータの回転方向を決める

```C++
inline void front_right_cw_ccw(PinStatus status)
```
```C++
inline void front_left_cw_ccw(PinStatus status)
```
```C++
inline void rear_left_cw_ccw(PinStatus status)
```
```C++
inline void rear_right_cw_ccw(PinStatus status)
```

| 変数名 | 型 | 想定される範囲 |
|:-----------|------------:|:------------:|
| value   | int        | 0 ~ 255    |
