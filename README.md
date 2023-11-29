# Kaggle-Titanic-0.76

2023年8月

Kaggle竞赛：多种机器学习方法预测泰坦尼克号事件生还者。
1. 预处理：对于缺失特征进行分类后的中位数填充，对于连续型特征做分箱，对于分类型特征做编号。
2. 特征工程：对特征进行统计衍生，再筛去低方差/共线性特征。
3. 建模：建立LR/RF模型，用交叉验证进行评估。

## 1.1. 处理缺失值和重复值

### 法一：
* 对分类变量缺失值：填充某个缺失值字符(NA)、用最多类别的进行填充
* 对连续变量缺失值：填充均值、中位数、众数

### 法二：
查看数据整体分布情况
* 数值型 .describe()
* 分类型 .describe(include = ['0'])

* Age：根据Sex,Pclass分类后的中位数来填充

## 1.2 数据可视化

* .groupby().count().unstack().plot()
* plt.hist()
* sns.kdeplot()
* sns.heatmap()
* ProfileReport()

## 1.3 创造新变量

* 提取部分字符串：把Name中的Title提取出来

## 2.1 模型搭建

### 2.1.1 分类变量 用pd.get_dummies(data)

### 2.1.2 分类变量编码 用LabelEncoder()

### 2.1.3 Age,Fare分箱

* pd.cut()

## 2.2 预测结果

### 2.2.1 Age均值填充，Age,Sex编码（ 0.76794 ）

### 2.2.2 Age均值填充，Age,Sex编码,Age改成Ageband（ 0.75358 ）

### 2.2.3 Age分类中位数填充，Name中提取称谓Title，isAlone（ 0.76555 ）

### 2.2.4 用RF，Age分类中位数填充，Name中提取称谓Title，isAlone（ 0.72488 ）

## 2.3 模型评估

* cross_val_score()
