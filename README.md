# easyKey 
为了满足不同的需求，每个文件夹都代表了不同版本适用于不同场景的的easyKey模块，他们的使用方法可能稍有不同，但放心，他们都很好理解，很好上手，并且下面的内容中会介绍各个版本的easyKey的使用方法
To meet diverse requirements, each folder contains a different version of the **easyKey** module, tailored for specific scenarios. While their usage may vary slightly, rest assured—all versions are intuitive, easy to understand, and quick to get started with. 
Detailed instructions for using each version of **easyKey** are provided below.
## easyKey v1
### how to use ?
You need to enable a timer and configure an interrupt callback triggered on timer overflow—here, a callback period of **1 ms** is recommended. After that, only three steps remain:

1. Place the `KEY_Tick()` function inside the timer callback function.
2. Initialize your key(s) using `KEY_Init()`, which returns a pointer to the key’s structure.
3. Use `KEY_UP(key)` to define the action triggered when the key is released.
``` c
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
{
    if( htim == &htim4 )
    {
        KEY_Tick();
    }
}
```
``` c
KEY key1 = KEY_Init(KeyGPIOx: GPIOB, KeyPIN: GPIO_PIN_12, KeyActiveLevel: 0);
```
```c
if(KEY_UP(key: key1))
{
    //write the thing you want to do
    HAL_GPIO_TogglePin(GPIOx: GPIOA, GPIO_Pin: GPIO_PIN_7);
}
```
Below is an example using STM32 (based on HAL library):

> Additional content is still under development and will be continuously enhanced.
