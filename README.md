# Verilog里的一些常见概念
## tips1 按位与/或 和 逻辑与/或
在verilog 和 C 中：
- 按位与是 & ；逻辑与是 && 。
- 同样的，按位或是 | ；逻辑或是 || 。
## tips2 按位取反和逻辑非
在verilog 和 C 中：
- 按位取反是~
- 逻辑取反是！
e.g: `XGpioPs_WritePin`函数，如果按下列代码：
`int led_state = 0`
`XGpioPs_WritePin(&Gpio, MIOLED0, ~led_state);`
这样会导致错误，因为~是按位取反，而`XGpioPs_WritePin`函数输入的是一个32位无符号整数。所以如果这样写的话输入就变成了一个32位的全1，即0xFFFFFFFF
故正确的应该为`XGpioPs_WritePin(&Gpio, MIOLED0, !led_state);`
