### Titanic 决策树模型

## 项目概述
本项目使用决策树分类器（Decision Tree Classifier）预测泰坦尼克号乘客的生存情况，数据包括乘客的年龄、性别、舱位等特征。我们通过数据预处理、模型训练、剪枝优化来提升模型的性能。

## 项目结构

- **titanic_data.csv**：包含泰坦尼克号乘客数据的 CSV 文件。
- **titanic_model.py**：包含数据预处理、模型训练和评估的 Python 代码。
- **titanic_predictions.csv**：包含测试集的预测结果。
- **README.md**：本文件。

## 运行步骤

1. **安装依赖**：
   运行以下命令安装所需的 Python 库：
   ```bash
   pip install -r requirements.txt
   ```

2. **数据预处理**：
   - 填充缺失值：年龄用均值填充，票价用均值填充，登船港口用最频繁的值填充。
   - 特征转换：使用 **One-Hot 编码** 转换分类特征（如性别、登船港口）。

3. **训练决策树模型**：
   - 使用 **Gini 指数** 作为划分标准。
   - 调整模型参数，使用 **交叉验证**（10折交叉验证）评估模型性能。
   - 使用 **剪枝**（`ccp_alpha`）减少过拟合，提升泛化能力。

4. **模型评估**：
   - 计算训练集准确率。
   - 通过交叉验证计算模型的平均准确率。
   - 使用剪枝后模型进行预测，计算测试集准确率。

5. **可视化决策树**：
   使用 **Graphviz** 绘制训练好的决策树，便于理解模型的决策过程。



## 结果分析

- **训练准确率**：模型在训练集上的准确率较高，表示模型拟合较好。
- **交叉验证准确率**：通过交叉验证获得大约 **81.94%** 的准确率，说明剪枝后模型的泛化能力较强。
- **剪枝效果**：选择了最佳 `ccp_alpha=0.00164`，有效避免了过拟合。

## 结论

通过决策树分类器并结合剪枝优化，我们成功提升了模型的泛化能力，避免了过拟合，模型在测试集上的表现较好。

## 进一步优化

- **特征工程**：可以尝试新增或调整特征，进一步提升模型性能。
- **超参数调优**：调节其他超参数如 `max_depth` 和 `min_samples_split` 以优化模型。
- **尝试其他模型**：如随机森林（Random Forest）或 XGBoost 可能会取得更好的结果。

---

**注意**：运行代码时，请确保将 `'titanic_data.csv'` 替换为实际数据文件路径，并安装所需库。