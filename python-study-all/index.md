# Python知识汇总


### 字典 dictionary

```python
# 遍历字典
for k,v in dict_test.items():
	print(k,v)
for key in dict_test.keys():
	print(k)
for value in dict_test.values():
	print(k)
for key in dict_test:
	print(key)

```

### 列表 list

```python
# 获取最大频繁项
list_test = [33,33,1,33,1,2]
frequently_num = max(set(list_test),key=list_test.count)
print(frequently_num)
# list循环取值
list1 = [1,2,3,4,5]
list2 = []
list2 = [i for i in list1]
print(list2)
# >>>>> [1,2,3,4,5]
# 错误例子【begin】-----------------------
list2 = list1
list2.append(6)
print(list1)
# >>>>> [1,2,3,4,5,6]
print(list2)
# >>>>> [1,2,3,4,5,6]
# 出现同时赋值【end】-----------------------
# 遍历等长list,  zip用法
for i, j in zip(list1,list2):
	print(i,j)
```

### lower()忽略大小写

```python
str_one="abCD"
str_two="ABcd"
print(str_two.lower()==str_one.lower())
```

---

### 日志

* 最近更新：字典、列表
* 日期：2023-2-19

