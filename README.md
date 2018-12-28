# student_and_teacher_classifier
通过科研人员论文项目等数据，训练识别导师/学生的分类器。代码包括特征选择基础、网格搜索确定特征选择方法参数、不平衡数据的处理（oversampling和undersampling）和pu-learning方法在此问题上的应用。

### 简要介绍本任务

本任务主要基于科研人员的论文数据以及基于论文数据产生的pagerank值、centrality等特征。

由于特征大多数都是由论文信息得到（这是实际项目中数据的限制），所以想利用特征选择方法看能够去除一些冗余特征。

另外，由于在项目中大概有17000个导师标签，但是没有学生标签（后来手动标了1000多个），存在严重的数据不平衡问题，所以想利用不平衡学习的方法解决。除此之外，在没有手动标数据之前，尝试了pu-learning的方法，效果会好很多。

### 具体包括以下文件：

featureSelectionBasic.ipynb:主要包括常用特征选择方法，有Filter、Wrapper和Embedded三类。

commonClassifer.ipynb：网格搜索确定特征选择的参数，但是这份代码里直接使用分类器训练的效果不好，问题在于训练集正例数目很多，但是负例数目很少，正例数据大概是负例数据的10倍。

underSamplingClassifier.ipynb:主要采用undersampling的方法解决数据不平衡的问题。

overSamplingClassifier.ipynb：主要采用oversampling的方法解决数据不平衡的问题。

puLearningPredict.ipynb: 使用positive and unlabeled learning的方法解决数据不平衡的问题。

baggingPU.py: 代码来自https://github.com/roywright/pu_learning/blob/master/baggingPU.py ，感谢作者


## 1、featureSelectionBasic

主要包括Filter、Wrapper和Embedded三类。

- Filter

主要包括方差分析、相关系数法、卡方检验、F检验和互信息法。

- Wrapper

主要包括递归特征消除法。

- Embedded

主要包括基于树模型的特征选择法和基于正则化的特征选择法。

## 2、commonClassifer

在特征选择方面，主要使用了Filter中的方差分析、Wrapper中的RFE和RFECV、Embedded中的L1正则化。

特征选择参数使用的是网格搜索。

## 3、underSamplingClassifier

主要使用random-under-sampling的方法解决数据不平衡的问题。

## 4、overSamplingClassifier

主要使用over-sampling的方法解决数据不平衡的问题，包括：SMOTE、AdaSyn和RandomOverSampling方法。

## 5、puLearningPredict

主要使用的是positive-unlabeled-learning的方法解决数据不平衡的问题，这里采用解决pu-learning问题的两种主流算法：pu-bagging和基于two-step思想的算法。

更详细的内容请移步本人博客：https://blog.csdn.net/quiet_girl/article/details/85259086
