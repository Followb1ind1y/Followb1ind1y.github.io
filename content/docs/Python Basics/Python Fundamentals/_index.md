---
weight: 2
title: "Python Fundamentals"
---
# **Python Fundamentals**

{{% hint warning %}}
这是一个Python基础知识总结文档，涵盖变量（Variables）、列表（Lists）、元组（Tuples）、集合（Sets）、字典（Dictionaries）、条件语句（If statements）、循环（Loops）、列表推导式（List comprehension）、函数（Functions）、类与继承（Classes & Inheritance）、装饰器（Decorators）及回调函数（Callbacks）等核心内容。
{{% /hint %}}

## **列表 (Lists)**

**列表 (Lists)** 是 **有序的 (ordered)**、**可变的 (mutable)** 值集合，这些值以逗号分隔并用方括号括起来。列表可以由许多不同类型的变量组成。

```python
# Creating a list
x = [3, "hello", 1.2]
print (x)
```
```
[3, 'hello', 1.2]
```

我们可以使用 `append` 函数将新的值添加到 **列表 (Lists)** 中：

```python
# Adding to a list
x.append(7)
print (x)
print (len(x))
```
```
[3, 'hello', 1.2, 7]
4
```

或者直接替换现有的值：
```python
# Replacing items in a list
x[1] = "bye"
print (x)
```
```
[3, 'bye', 1.2, 7]
```

并可以直接对 **列表 (list)** 执行操作：
```python
# Operations
y = [2.4, "world"]
z = x + y
print (z)
```
```
[3, 'bye', 1.2, 7, 2.4, 'world']

```

## **元组 (Tuples)**

**元组 (Tuples)** 是 **有序 (ordered)** 且 **不可变 (immutable)** 的集合。我们将使用元组来存储 **永远不会改变** 的值。

```python
# Creating a tuple
x = (3.0, "hello") # tuples start and end with ()
print (x)
```
```
(3.0, 'hello')
```
```python
# Adding values to a tuple
x = x + (5.6, 4)
print (x)
```
```
(3.0, 'hello', 5.6, 4)
```
```python
# Try to change (it won't work and we get an error)
x[0] = 1.2
```
```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
----> 1 x[0] = 1.2
TypeError: 'tuple' object does not support item assignment
```

## **集合 (Sets)**

**集合(sets)** 是 **无序(unordered)** 且 **可变(mutable)** 的。但是，集合中的每个项目必须是 **唯一(unique)** 的。

```python
# Sets
text = "Learn ML with Made With ML"
print (set(text))
print (set(text.split(" ")))
```
```
{'e', 'M', ' ', "r", "w", 'd', 'a', 'h', 't', 'i', 'L', 'n', "w"}
{'with', 'Learn', 'ML', 'Made', 'With'}
```

## **字典 (Dictionaries)**

**字典 (Dictionaries)** 是 **无序 (unordered)** 且 **可变 (mutable)** 的 **键值对(key-value pair)** 集合。我们可以根据 **键(key)** 检索 **值(value)**，但字典不能有两个相同的键。

```python
# Creating a dictionary
person = {"name": "Goku", "eye_color": "brown"}
print (person)
print (person["name"])
print (person["eye_color"])
```
```
{"name": "Goku", "eye_color": "brown"}
Goku
brown
```
```python
# Changing the value for a key
person["eye_color"] = "green"
print (person)
```
```
{"name": "Goku", "eye_color": "green"}
```
```python
# Adding new key-value pairs
person["age"] = 24
print (person)
```
```
{"name": "Goku", "eye_color": "green", "age": 24}
```
```python
# Length of a dictionary
print (len(person))
```
```
3
```

## **索引 (Indexing)**

通过列表的 **索引(indexing)** 和 **切片 (slicing)**，我们可以检索列表中的特定值。请注意，索引可以是正数（**从 0 开始**）或负数（-1 及以下，其中 **-1 是列表中的最后一项**）。

```python
# Indexing
x = [3, "hello", 1.2]
print ("x[0]: ", x[0])
print ("x[1]: ", x[1])
print ("x[-1]: ", x[-1]) # the last item
print ("x[-2]: ", x[-2]) # the second to last item
```
```
x[0]:  3
x[1]:  hello
x[-1]:  1.2
x[-2]:  hello
```
```python
# Slicing
print ("x[:]: ", x[:]) # all indices
print ("x[1:]: ", x[1:]) # index 1 to the end of the list
print ("x[1:2]: ", x[1:2]) # index 1 to index 2 (not including index 2)
print ("x[:-1]: ", x[:-1]) # index 0 to last index (not including last index)
```
```
x[:]:  [3, 'hello', 1.2]
x[1:]:  ['hello', 1.2]
x[1:2]:  ['hello']
x[:-1]:  [3, 'hello']
```

## **if 语句 (if statements)**

我们可以使用 `if` 语句有条件地执行某项操作。条件由单词 `if`、`elif`（代表 else if）和 `else` 定义。我们可以根据需要使用任意数量的 `elif` 语句。每个条件下方的缩进代码是条件为 `True` 时将执行的代码。

```python
# If statement
x = 4
if x < 1:
    score = "low"
elif x <= 4: # elif = else if
    score = "medium"
else:
    score = "high"
print (score)
```
```
medium
```
```python
# If statement with a boolean
x = True
if x:
    print ("it worked")
```
```
it worked
```

## **循环语句 (Loop)**

### **For loops**
`for` 循环可以迭代值集合（列表 (list)、元组 (tuple)、字典 (dictionaries)等）。缩进的代码针对值集合中的 **每个项目** 执行。
```python
# For loop
veggies = ["carrots", "broccoli", "beans"]
for veggie in veggies:
    print (veggie)
```
```
carrots
broccoli
beans
```
当循环遇到 `break` 命令时，**循环将立即终止**。如果列表中还有更多项目，则不会处理它们。
```python
# `break` from a for loop
veggies = ["carrots", "broccoli", "beans"]
for veggie in veggies:
    if veggie == "broccoli":
        break
    print (veggie)
```
```
carrots
```
当循环遇到 `continue` 命令时，循环将**仅跳过列表中该项目的所有其他操作**。如果列表中还有更多项目，循环将正常继续。
```python
# `continue` to the next iteration
veggies = ["carrots", "broccoli", "beans"]
for veggie in veggies:
    if veggie == "broccoli":
        continue
    print (veggie)
```
```
carrots
beans
```
### **While loops**
只要条件为 `True`，`while` 循环就可以重复执行。我们也可以在 `while` 循环中使用 `continue` 和 `break` 命令。
```python
# While loop
x = 3
while x > 0:
    x -= 1 # same as x = x - 1
    print (x)
```
```
2
1
0
```

## **列表推导式 (list comprehension) 和生成器表达式 (generator expression)**

**快速构建列表或生成器**，尤其适合在数据处理或特征工程中清洗数据或生成特定序列。

* 列表推导式 (list comprehension)：返回一个完整的列表。
* 生成器表达式 (generator expression)：返回一个惰性生成器，节省内存。


```python
# 过滤列表中的偶数
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = [x for x in numbers if x % 2 == 0]
print(even_numbers)  # [2, 4, 6]

# 生成器表达式（惰性求值）
gen = (x**2 for x in range(5))  # 不占用大量内存
for val in gen:
    print(val)
```
```
[2, 4, 6]
0
1
4
9
16
```

## **Lambda 函数和 map, filter 的使用**

* `Lambda函数`：定义简洁的匿名函数，适合简单逻辑。(e.g. `func = lambda var1 var2 : function` => `func(var1, var2)`)
* `map`：对可迭代对象中的每个元素应用函数。
* `filter`：筛选符合条件的元素。


```python
from functools import reduce

# Lambda函数示例
add = lambda x, y: x + y
print(add(3, 5))  # 8

# map: 计算平方
squares = list(map(lambda x: x**2, [1, 2, 3]))
print(squares)  # [1, 4, 9]

# filter: 筛选出大于2的元素
filtered = list(filter(lambda x: x > 2, [1, 2, 3, 4]))
print(filtered)  # [3, 4]
```

```
8
[1, 4, 9]
[3, 4]
```
## **函数 (Function) 封装**

在ML项目中**封装代码逻辑**，便于维护和复用。例如，封装数据预处理步骤或模型训练流程。


```python
def preprocess_data(data):
    preprocessed_data = data.dropna()
    return preprocessed_data

# <---------- Usage ---------->
# cleaned_data = preprocess_data(raw_data)
```

`def f(*args, **kwargs)` 是另一种定义函数的方式，用来接收可变数量的参数。它允许函数在调用时传入任意数量的位置参数和关键字参数，从而使函数更加灵活。
* `*args`: 可变长度位置参数，接收任意数量的未命名参数 (**arguments**)，作为一个元组。
* `**kwargs`: 可变长度关键字参数，接收任意数量的命名参数 (**keyword arguments**)，作为一个字典。


```python
def f(*args, **kwargs):
    # 从位置参数中提取第一个值，赋值给变量 x
    x = args[0]
    # 从关键字参数中获取键 "y" 的值，若不存在返回 None
    y = kwargs.get("y")
    print (f"x: {x}, y: {y}")

# 调用函数 f，传入一个位置参数 5 和一个关键字参数 y=2
f(5, y=2)
```
```
x: 5, y: 2
```

## **类 (Class) 封装**


```python
class DataHandler:
    def __init__(self, filepath):
        self.filepath = filepath

    def load_data(self):
        print(f"Loading data from {self.filepath}...")
        return {"data": [1, 2, 3, 4]}

    def preprocess_data(self, data):
        return [x * 2 for x in data]

# <---------- Usage ---------->
# new_handler = DataHandler('data.csv')
# new_data = new_handler.load_data()
# preprocess_data = new_handler.preprocess_data(new_data['data'])
```

### **继承 (Inheritance)**

继承用于让一个类（子类）从另一个类（父类）中获得 **属性(properties)** 和 **方法(methods)**，从而实现代码复用和扩展。

* 子类继承父类的方法和属性。
* 使用 `super()` 调用父类的方法。
* 方法重写：子类可重写父类的方法实现。


```python
# 定义一个基础模型类
class BaseModel:
    def __init__(self, name):
        self.name = name

    def train(self):
        print(f"{self.name} is training...")

    def test(self):
        print(f"{self.name} is testing...")

# 子类继承基础模型类
class RegressionModel(BaseModel):
    def __init__(self, name, num_features):
        super().__init__(name)
        self.num_features = num_features

    def train_1(self):
        super().train()
        print(f"Training a regression model with {self.num_features} features.")

# 使用子类
model = RegressionModel("LinearRegression", 10)
model.train()
model.test()
```
```
LinearRegression is training...
LinearRegression is testing...
```

### **方法 (Methods)**

* **实例方法 (Instance Method)**：实例方法的第一个参数是 `self`，用于访问实例属性和其他实例方法。它需要通过实例对象调用，依赖于具体的实例状态。当方法需要操作实例的属性（如 `self.name`）或依赖于实例的状态时，实例方法是最合适的选择。
* **类方法 (Class Method)**：类方法的第一个参数是 `cls`，表示类本身（而不是实例）。它使用 `@classmethod` 装饰器修饰，可以通过类对象或实例对象调用。当方法需要操作类级别的状态（如 `total_models`）而不依赖于任何具体实例时，类方法可以保持逻辑的清晰和一致性。
* **静态方法 (Static Method)**：使用 `@staticmethod`，与类或实例 (`self` 或 `cls`)无绑定，仅实现功能逻辑。当方法的逻辑与类相关，但完全独立于类或实例的状态时，静态方法可以避免无意义的参数（如 `self` 或 `cls`），提高代码的简洁性。


```python
class MLModel:
    total_models = 0  # 类属性

    def __init__(self, name):
        self.name = name
        MLModel.total_models += 1

    def display(self):  # 实例方法
        print(f"Model Name: {self.name}")

    @classmethod
    def get_total_models(cls):  # 类方法
        print(f"Total models created: {cls.total_models}")

    @staticmethod
    def utility_function(x):    # 静态方法
        return x**2

# 使用
model = MLModel("RandomForest")
model.display()
MLModel.get_total_models()
print(MLModel.utility_function(5))
```
```
Model Name: RandomForest
Total models created: 1
25
```

### **装饰器 (Decorators)**

装饰器是一种函数，接受另一个函数或方法作为输入并返回一个修改后的函数，用于动态扩展功能。

```
@decorator
def function():
    pass
```
等价于：
```
def function():
    pass
function = decorator(function)
```


```python
import time

# 定义一个装饰器
def timer_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Function '{func.__name__}' executed in {end_time - start_time:.4f}s")
        return result
    return wrapper

# 装饰训练函数
class MLModel:
    @timer_decorator
    def train(self, data):
        print("Training model...")
        time.sleep(1)  # 模拟训练时间
        return "Training Complete"

model = MLModel()
print(model.train([]))
```
```
Training model...
Function 'train' executed in 1.0015s
Training Complete
```

### **回调函数 (Callbacks)**

回调是一个函数作为参数传递给另一个函数，并在适当时调用。它在机器学习中常用于动态调整训练流程（如早停、学习率调整）。


```python
class TrainingCallback:
    def on_epoch_start(self, epoch):
        print(f"Epoch {epoch} started.")

    def on_epoch_end(self, epoch, loss):
        print(f"Epoch {epoch} ended with loss: {loss}.")

# 使用回调
class MLTrainer:
    def __init__(self, callback=None):
        self.callback = callback

    def train(self, epochs):
        for epoch in range(epochs):
            if self.callback:
                self.callback.on_epoch_start(epoch)
            # 模拟训练过程
            loss = 0.01 * (epochs - epoch)
            if self.callback:
                self.callback.on_epoch_end(epoch, loss)

# 测试回调
callback = TrainingCallback()
trainer = MLTrainer(callback)
trainer.train(3)
```
```
Epoch 0 started.
Epoch 0 ended with loss: 0.03.
Epoch 1 started.
Epoch 1 ended with loss: 0.02.
Epoch 2 started.
Epoch 2 ended with loss: 0.01.
```

## **模块 (Module) 封装**

```
project/
    ├── data_processing.py  # Contains functions for data processing
    ├── model_training.py   # Contains model training logic
    ├── evaluation.py       # Contains evaluation methods
```


```python
# <---------- Usage ---------->

# <---------- data_processing.py ---------->

# def clean_data(data):
#     """Clean the data by dropping missing values."""
#     print("Cleaning data...")
#     return data.dropna()

# <---------- main.py ---------->

# import data_processing as dp

# data = dp.load_data("data.csv")
# cleaned_data = dp.clean_data(data)
```

## **异步编程 (Asynchronous Programming)**

在训练、数据下载、或者与API通信时**异步执行**，提高性能。

* `async` 用于定义一个异步函数。使用 `async def` 定义，表示该函数会返回一个协程对象。
* `await` 用于调用另一个异步函数，并等待其执行完成，直到结果返回。
* `asyncio` 库提供了一个框架来实现异步编程。

```python
import nest_asyncio
import asyncio
nest_asyncio.apply()  # Allows nested use of asyncio.run [Only for Jupyter Notebook]

# 定义一个异步函数
async def say_hello():
    print("Hello")
    await asyncio.sleep(1)  # 模拟一个耗时的异步操作
    print("World")

# 运行异步任务
asyncio.run(say_hello())
```
```
Hello
World
```


```python
import asyncio

# 定义异步任务
async def fetch_data():
    print("Fetching data...")
    await asyncio.sleep(2)  # 模拟耗时的异步操作
    return "Data fetched"

async def process_data():
    print("Processing data...")
    await asyncio.sleep(1)  # 模拟耗时的异步操作
    return "Data processed"

# 主程序
async def main():
    data_task = asyncio.create_task(fetch_data())  # 启动任务1
    process_task = asyncio.create_task(process_data())  # 启动任务2

    result1 = await data_task  # 等待任务1完成
    result2 = await process_task  # 等待任务2完成

    print(result1)
    print(result2)

# 启动事件循环
asyncio.run(main())
```
```
Fetching data...
Processing data...
Data fetched
Data processed
```