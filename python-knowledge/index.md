# Python知识汇总

> All Python knowledge
## Python关键字
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
### sort_values
```python
DataFrame.sort_values(by='##',axis=0,ascending=True inplace=False, na_position='last')  # 列，升降排序，替换，缺失值
```

## Pandas相关
### isin()
```python
# 取出存在或者不存在列表中的数据
lst = ['1','3']
data = {'num': ['1', '2', '3', '4', '5']}
df = pd.DataFrame(data)
not_list_df = df[~df['num'].isin(lst)] #~为反向取值 
in_list_df = df[df['num'].isin(lst)]
```
### 使用fillna() 将空值替换为空字符串
- 一般来说当后端返回json格式数据时，空值NaN并不方便处理，所以要转换成空字符串
```python
df.fillna('', inplace=True)  # 替换空字符串
```
### 使用dropna() 去除空值
```python
df.dropna(subset=['col_name'],inplace=True)  # inplace 是否直接覆盖原表
```
### 使用isnull() 取空值
```python
# 取到col_name为空的所有数据
df_null = df[df['col_name'].isnull()]
# 取到col_name_one或col_name_two为空的所有数据
df_null = df[(df['col_name_one'].isnull()) | (df['col_name_one'].isnull())]
```
## Python连接数据库
```python
# 导入pymysql库
import pymysql
# 创建连接
db = pymysql.connect(
    host="127.0.0.1",
    user="username",
    password="password",
    database="database",
    port=3360
)
# 创建游标，对数据库进行操作
cursor = db.cursor()
# 查询某张表格的数据，显示一条
sql = "SELECT * FROM table_name LIMIT 1"
# 执行sql
cursor.execute(sql)
# 获取查询后的数据
result = cursor.fetchall()
# 遍历输出，row类型是元组
for row in result:
	print(row)
```
## requests库
### 超时设置
```python
import requests
import json
url = "xxx"  # 请求链接
data = {"data":"data"} # 请求参数
timeout = (1,1) # 连接超时/读取超时 
timeout = 1 # 通用超时，但是有时候会不起效果
# 请求
response = requests.post(url,data=json.dumps(data),timeout=timeout).json()
```
