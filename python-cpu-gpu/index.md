# Python中CPU、GPU判断

## 判断代码运行环境
```python
import torch
# 函数
def CPU_or_GPU():
    device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
    if device.type == 'cuda':
        return 'GPU'
    else:
        return 'CPU'
```
## 判断运行环境的内存/显存容量
```python
from pynvml import *
import psutil
# 空闲显存
def GPU_free():
    nvmlInit()  # 初始化
    handle = nvmlDeviceGetHandleByIndex(0)
    info = nvmlDeviceGetMemoryInfo(handle)
    free_memory = info.free
    nvmlShutdown()
    return free_memory

# 空闲内存
def CPU_free():
    mem = psutil.virtual_memory()
    free_memory = mem.available
    return free_memory

# 空闲显存容量是否大于4GB
def GPU_avil():
    retry = 1
    # 重试1次
    while retry:
        free_memory = GPU_free()
        if free_memory > 4294967296:
            return 1
        else:
            retry -=1
    return 0

# 空闲内存容量是否大于4GB
def CPU_avil():
    retry = 1
    # 重试1次
    while retry:
        free_memory = CPU_free()
        if free_memory > 4294967296:
            return 1
        else:
            retry -= 1
    return 0
```

## 结合使用
1. 一般的，在服务器中使用某个功能都需要判断内存或者显存容量
2. 目的是为了防止沾满，导致宕机等错误
```python
import torch
# 只要更改CPU_or_GPU函数即可
def CPU_or_GPU():
    device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
    if device.type == 'cuda':
        if not GPU_avil():
            return 1
    else:
        if not CPU_avil():
            return 2
    return 0
# 调用
msg = {
  1:"GPU显存不足"
  2:"CPU内存不足"
}
code_id =  CPU_or_GPU()
# code_id 为0时则不进入判断
if code_id:
  print(msg[code_id])
else:
  print("pass")
```
