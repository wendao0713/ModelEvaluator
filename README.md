### 项目简介

本项目探讨了统计学习中多种分类方法在疾病诊断中的应用。本项目选用来自UCI机器学习王章的成年女性是否患糖尿病的数据，基于Python语言构造出包含解决异常语句的分类模型评估器`ModelEvaluator`类。该评估器包含LDA、QDA、逻辑斯蒂回归、KNN和随机森林5个分类模型，类中包含的方法可以用k折交叉验证的方法实现模型参数调优以及模型效果评价，并对调优过程、单个分类器的表现、多个分类器的对比进行可视化输出，在评价模型效果时具体使用分类正确率、召回率、F1分数等评价指标。类中包含的主要方法如下：

|             **方法名**             |                         **方法参数**                         |                         **方法作用**                         |
| :--------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        tune_hyperparameters        | model_name：方法名   param_grid：超参数列表   param_count：超参数的个数   cv：交叉验证的折数 | 针对指定模型进行超参数调优，默认调优的超参数个数为2，使用10折交叉验证 |
| plot_hyperparameter_tuning_results | cv_results：通过tune_hyperparameters生成的交叉验证得分列表   param_grid：超参数列表   param_count：超参数的个数 | 可视化超参数调优结果，目前仅支持小于等于2的参数个数。如果参数个数为1，使用折线图；如果参数个数为2，使用热图。 |
|          evaluate_models           |                              /                               |                      评估所有模型的性能                      |
|         train_and_evaluate         | model: 分类模型   data_train：训练集   data_test：测试集   Outcome_test：测试集中的目标变量   model_name：模型名称 |                      训练和评估单个模型                      |
|       plot_model_performance       |                     model_name：模型名称                     | 用于可视化指定模型在每个测试集上的表现   ，以堆叠条形图和折线图的形式展示不同评估指标（如准确率、精确度、召回率和F1分数）。 |
|        plot_mean_cv_scores         |                              /                               | 展示并对比类中所有模型的平均交叉验证分数，以折线图的形式展示所有模型的平均评估指标。 |



### 运行环境和依赖包版本

- Python版本：3.8 或更高
- 主要依赖包：
  - scikit-learn：0.24.1 或更高
  - pandas：1.2.1 或更高
  - numpy：1.19.5 或更高
  - matplotlib：3.3.4 或更高
  - seaborn：0.11.1 或更高

### 复现步骤

1. **环境配置**：

   - 确保已安装Python 3.8或更高版本。

   - 安装所需的依赖包。可以使用以下命令安装：

     ```bash
     pip install scikit-learn pandas numpy matplotlib seaborn
     ```

2. **数据准备**：

   - 准备用于分类的数据集。在本项目中，使用的是成年女性糖尿病诊断数据集。
   - 确保数据集格式正确，并且已经进行了适当的预处理。

3. **代码执行**：

   - 运行`ModelEvaluator`类的实例化和模型评估代码。
   - 对所需的模型使用`  tune_hyperparameters`方法进行参数调优，并使用`plot_hyperparameter_tuning_results`方法可视化调优结果。
   - 使用`plot_model_performance`和`plot_mean_cv_scores`方法可视化模型性能和比较不同模型的效果。

4. **结果分析**：

   - 分析和解释模型评估和调优的结果。
   - 对比调优前后的模型性能，以确定最佳的模型选择和参数配置。

### 注意事项

- 确保所有的步骤按照顺序执行，以避免依赖问题。
- 在对数据进行操作时，特别注意数据的清洗和预处理步骤，以确保模型评估的准确性。
- 在解释模型结果时，考虑到不同模型可能适用于不同类型的数据分布和特征，因此选择合适的模型是关键。
