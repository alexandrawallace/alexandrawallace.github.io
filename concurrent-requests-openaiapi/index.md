# Python多线程请求OpenAI API

## 通过threading库实现多线程请求
```python
import threading
import queue
import openai
import os
import time
# 设置 OpenAI API 密钥
openai.api_key = "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"
# 定义线程处理函数
def process_data(data, result_queue):
    messages = [{
    "role": "assistant",                
    "content": data
    }]
    # 请求 OpenAI 的 API 接口
    response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo-0301",   # 选择模型，详见 https://platform.openai.com/docs/api-reference/models
    messages=messages,              # 输入原文
    temperature=0.0,            # 控制结果的随机性，如果希望结果更有创意可以尝试0.9，或者希望有固定结果可以尝试0.0
    max_tokens=100,             # 回答文本最大 tokens 数
    top_p=1,                    # 一个可用于代替temperature的参数，对应机器学习中nucleus sampling，如果设置0.1意味着只考虑构成前10%概率质量的tokens
    frequency_penalty=2.0,      # -2.0~2.0之间的数字，正值会根据新tokens在文本中的现有频率对其进行惩罚，从而降低模型逐字重复同一行的可能性
    presence_penalty=0.0,        # -2.0~2.0之间的数字，正值会根据到目前为止是否出现在文本中来惩罚新tokens，从而增加模型谈论新主题的可能性
    stream = False
    )
    
    result = response["choices"][0]["message"]["content"]
    # print(result)
    result_list.append({'data':str(data),"result":str(result)})
    # 将结果存储到队列中
    # result_queue.put((data, result))
# 定义数据列表
data_list = ["输出1", "输出2", "输出3", "输出4", "输出5"]
# 创建队列和结果列表
# result_queue = queue.Queue()
result_list = []
# 启动线程
threads = []
for i, data in enumerate(data_list):
    # print(data)
    t = threading.Thread(target=process_data, args=(data, result_queue))
    threads.append(t)
    t.start()
# 等待所有线程结束
for t in threads:
    t.join()
# 队列有存入有问题不写了
# 按照列表顺序返回结果列表
print(result_list)
```
## 说明
- Newtea
