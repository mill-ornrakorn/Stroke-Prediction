# Stroke Prediction
 
## 📁Dataset
<p align="center">
    <img src="https://github.com/mill-ornrakorn/Stroke-Prediction/blob/main/pic%20for%20readme/dataset.png?raw=true" alt= "df" >
</p>

ข้อมูลนี้เกี่ยวกับ**โรคหลอดเลือดสมอง (Stroke)** มาจาก [Stroke Prediction Dataset ใน kaggle](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset) ซึ่งประกอบไปด้วย label คือ 0 = ไม่เป็น Stroke และ 1 = เป็น Stroke

## 📝ตารางสรุปผล:

**ตารางที่ 1:** model ที่ใช้ข้อมูลทั้งหมดเลย (Imbalanced)
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 1.   |    Decision Tree    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)  | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 92% | Class 0: 96%, Class 1: 15% | Class 0: 95%, Class 1: 18%  | Class 0: 96%, Class 1: 16%  | 56%
| 2.   |   Random Forest    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)  | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 95% | Class 0: 96%, Class 1: 50% | Class 0: 100%, Class 1: 1%  | Class 0: 98%, Class 1: 3%  | 77%
| 3.   |   XGBoost    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)  | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 95% | Class 0: 96%, Class 1: 25% | Class 0: 99%, Class 1: 6%  | Class 0: 97%, Class 1: 10%  | 77%


**ตารางที่ 2:** model ที่ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 1.   |    Decision Tree    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling  | 70% = Class 0: 169 rows, Class 1: 165 rows |  30% = Class 0: 44 rows, Class 1: 40 rows | - | 65% | Class 0: 94%, Class 1: 65% | Class 0: 62%, Class 1: 68%  | Class 0: 63%, Class 1: 67%  | 65%
| 2.   |   Random Forest    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling  |  70% = Class 0: 169 rows, Class 1: 165 rows |  30% = Class 0: 44 rows, Class 1: 40 rows | - | 69% | Class 0: 72%, Class 1: 67% | Class 0: 57%, Class 1: 80%  | Class 0: 64%, Class 1: 73%  | 79%
| 3.   |   XGBoost    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling  |  70% = Class 0: 169 rows, Class 1: 165 rows |  30% = Class 0: 44 rows, Class 1: 40 rows | - | 69% | Class 0: 68%, Class 1: 70% | Class 0: 68%, Class 1: 70%  | Class 0: 68%, Class 1: 70%  | 75%

**ตารางที่ 3:** model ที่ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 1.   |    Decision Tree    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling |  Class 0: 3762 rows, Class 1: 3762 rows |  Class 0: 937 rows, Class 1: 45 rows | ทำ Over-sampling เฉพาะ train set | 92% | Class 0: 96%, Class 1: 13% | Class 0: 96%, Class 1: 11%  | Class 0: 96%, Class 1: 12%  | 54%
| 2.   |   Random Forest    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling  |  Class 0: 3762 rows, Class 1: 3762 rows |  Class 0: 937 rows, Class 1: 45 rows | ทำ Over-sampling เฉพาะ train set | 95% | Class 0: 95%, Class 1: 9% | Class 0: 99%, Class 1: 2%  | Class 0: 97%, Class 1: 4%  | 77%
| 3.   |   XGBoost    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling  |  Class 0: 3762 rows, Class 1: 3762 rows |  Class 0: 937 rows, Class 1: 45 rows | ทำ Over-sampling เฉพาะ train set | 94% | Class 0: 96%, Class 1: 11% | Class 0: 98%, Class 1: 4%  | Class 0: 97%, Class 1: 6%  | 80%


**ตารางที่ 4:** model ที่ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight 
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 1.   |    Decision Tree    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight   | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 93% | Class 0: 96%, Class 1: 16% | Class 0: 97%, Class 1: 13%  | Class 0: 96%, Class 1: 15%  | 55%
| 2.   |   Random Forest    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight   | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 95% | Class 0: 96%, Class 1: 33% | Class 0: 100%, Class 1: 1%  | Class 0: 98%, Class 1: 3%  | 77%
| 3.   |   XGBoost    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight   | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 94% | Class 0: 96%, Class 1: 22% | Class 0: 97%, Class 1: 16%  | Class 0: 97%, Class 1: 19%  | 76%