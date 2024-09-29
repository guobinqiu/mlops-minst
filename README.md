# mlops-minst

## mlops架构图

<img width="946" alt="image" src="https://github.com/user-attachments/assets/48da476a-1c68-440b-a4ac-d1b9476079ff">

## kubeflow组件说明

Component | Install Level | Function
--- | --- | ---
Kubeflow Pipelines | Required | 对多个有序任务进行串行处理
Kubeflow Training Operator | Required | 执行某个训练任务
KServe | Required | 模型部署和访问
Kubeflow Model Registry | Recommended | 模型版本控制
Kubeflow Katib | Recommended | 超参数(用户在训练前手动设定的参数)调优
Kubeflow MPI Operator | Recommended | 并行处理某个任务(如:对训练集分片后并行处理)
Kubeflow Notebooks | Optional | 一个web ide在线编写Pipeline或者MPI的执行代码
Kubeflow Spark Operator | Optional | 运行Apache Spark 作业

Kubeflow Piplines通常可拆成3阶段任务:
1. 数据准备任务
2. 训练任务 (也可以使用Kubeflow Training Operator, 主要区别: Kubeflow Training Operator任务是声明式的, pipeline任务是编程式的)
3. 模型部署任务 (调用KServe提供的服务)

## 基于minst数字样本搭建mlops环境

目标: 让minst模型运行在mlops环境下, 模型部署使用KServe(暂不使用model mash), 输出模型保存在本地存储上, 最终输出的模型可以正确识别手写数字
