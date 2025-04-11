# 实验报告 - Pandas 数据操作练习

## 一、实验目的
阐述本次实验的主要目的，可参考任务目的部分。

•	熟悉 Pandas 的数据结构（DataFrame）。
•	掌握数据的读取和写入操作。
•	学会数据清洗，包括处理缺失值、异常值。
•	能够进行数据的基本统计分析和复杂的数据转换。
•	了解如何使用 Pandas 进行数据可视化。


## 二、实验步骤
详细描述你完成每个任务的步骤和方法，可结合代码进行说明。

### 任务 1: 读取数据
说明你使用的读取数据的函数和过程。

调用 load_data 函数，该函数使用 ```pd.read_csv('data.csv')```读取名为 data.csv 的文件。
返回一个包含学生信息的 DataFrame。

```
def load_data():

    return pd.read_csv('data.csv')
```  

### 任务 2: 查看数据基本信息
描述如何查看数据的基本信息。

调用 ```show_basic_info(data)``` 函数，传入读取的数据。
在函数中，使用 ```data.info()``` 打印数据的基本信息。

```
def show_basic_info(data):

    print("数据基本信息：")
  
    data.info()
```

### 任务 3: 处理缺失值
说明你找出缺失值列和填充缺失值的方法。

 handle_missing_values(data) 函数中，使用 data.isnull().any() 确定哪些列包含缺失值。
遍历这些列，判断其数据类型是否为数值类型。
如果是数值列，则使用 fillna(data[col].mean()) 来填充缺失值。

```
def handle_missing_values(data):

    missing_columns = data.columns[data.isnull().any()].tolist()
    
    for col in missing_columns:
    
        if pd.api.types.is_numeric_dtype(data[col]):
        
            data[col] = data[col].fillna(data[col].mean())
            
    return data
 ```
   
### 任务 4: 数据统计分析
说明你计算数值列均值、中位数和标准差的方法。

在某个函数中，对 DataFrame 的数值列进行分析。
使用 ```data[['成绩', '年龄']].mean()``` 计算均值，
```data[['成绩', '年龄']].median()``` 计算中位数，
```data[['成绩', '年龄']].std()``` 计算标准差。

```
def basic_statistics(data):

    print("均值：")
    
    print(data[['成绩', '年龄']].mean())
    
    print("中位数：")
    
    print(data[['成绩', '年龄']].median())
    
    print("标准差：")
    
    print(data[['成绩', '年龄']].std())
```

### 任务 5: 数据可视化
描述你选择的数值列和绘制直方图的过程。

导入 matplotlib.pyplot。
在某个函数中，使用 ```plt.hist(data['成绩'], bins=5)``` 绘制成绩的直方图。
设置标题、横轴标签和纵轴标签，最后调用 ```plt.show()``` 显示图形。

```
def plot_histogram(data):

    plt.hist(data['成绩'], bins=5, color='skyblue', edgecolor='black')
    
    plt.title('成绩分布直方图')
    
    plt.xlabel('成绩')
    
    plt.ylabel('频数')
    
    plt.show()
```

### 任务 6: 数据保存
说明你保存处理后数据的方法。

在某个函数中调用 ```data.to_csv('processed_data.csv', index=False, encoding='utf-8')```。
将处理好的数据保存至名为 processed_data.csv 的新文件中。

```
def save_data(data):
    data.to_csv('processed_data.csv', index=False, encoding='utf-8')
```

## 三、实验结果
展示每个任务的结果，可使用表格或图表进行呈现。

### 任务 1: 读取数据
展示读取的数据的基本信息（如列名、行数等）。

列名	数据类型	非空值数量	示例值
姓名	object	    5	       张三
年龄	float64	    4    	 25.0
成绩	float64	    5    	 85.5
城市	object	    5	       北京


### 任务 2: 查看数据基本信息
粘贴数据的基本信息输出。

数据基本信息：
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 4 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   姓名      5 non-null      object 
 1   年龄      4 non-null      float64
 2   成绩      5 non-null      float64
 3   城市      5 non-null      object 
dtypes: float64(2), object(2)
memory usage: 168.0+ bytes
```

### 任务 3: 处理缺失值
说明处理后缺失值的情况。

在原始数据中，年龄 列有 1 个缺失值，处理后，缺失值用均值填充。

### 任务 4: 数据统计分析
列出数值列的均值、中位数和标准差。

年龄 列的均值: 26.25, 中位数: 26.25, 标准差: 3.031088913245535
成绩 列的均值: 86.8, 中位数: 88.0, 标准差: 5.227332015474051

### 任务 5: 数据可视化
插入绘制的直方图。

![image](https://github.com/user-attachments/assets/d4890926-2c77-4fc0-9fd9-1e6c347dae3b)

### 任务 6: 数据保存
说明保存的文件路径和文件名。

文件名：processed_data.csv
保存路径：当前工作目录（所有相关代码在同一目录下执行）。

## 四、总结
总结本次实验的收获和体会，分析遇到的问题及解决方法，对 Pandas 数据操作的理解和认识。

通过以上各个任务的执行，熟悉了数据从读取、处理、分析到可视化和保存的完整流程。在每个步骤中，采用了 Pandas 库的基本操作，完成了数据的读取、缺失值处理、统计分析、数据可视化和最终的数据保存，为未来的数据分析奠定了基础。


文件读取和保存路径问题：

在操作 CSV 文件时，最初未指定正确的路径，导致文件未能正确读取或保存。通过准确指定文件路径和检查当前工作目录，解决了此问题。  

Pandas 提供丰富的数据结构和函数，使得数据处理变得直观而高效。无论是基础的读取、保存，还是复杂的数据清洗、转换和分析，都能够轻松实现。对于数据科学及数据分析领域来说，Pandas 是一个不可或缺的基础工具。它与 NumPy、Matplotlib 等其他数据分析库的结合，使得数据科学家能够更全面地完成数据分析任务。
