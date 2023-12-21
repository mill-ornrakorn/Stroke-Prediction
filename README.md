# Stroke Prediction
 
## 📁Dataset
<p align="center">
    <img src="https://github.com/mill-ornrakorn/Stroke-Prediction/blob/main/pic%20for%20readme/dataset.png?raw=true" alt= "df" >
</p>

ข้อมูลนี้เกี่ยวกับ**โรคหลอดเลือดสมอง (Stroke)** มาจาก [Stroke Prediction Dataset ใน kaggle](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset) ซึ่งประกอบไปด้วย label คือ 0 = ไม่เป็น Stroke และ 1 = เป็น Stroke

## 🔎ความท้าทาย:
❗❗ ข้อมูลชุดนี้ Imbalanced มากกกกกก ทำให้การ train model มีความยากขึ้น ดังรูปกราฟต่อไปนี้

<p align="center">
    <img src="https://github.com/mill-ornrakorn/Stroke-Prediction/blob/main/pic%20for%20readme/stroke_plot.png?raw=true" alt= "stroke_plot" >
</p>

ข้อมูลทั้งหมดมี 4908 rows ประกอบด้วย label ดังนี้ 0 = ไม่เป็น Stroke, 1 = เป็น Stroke ซึ่ง label 0 มีจำนวน 4699 rows คิดเป็น 96% ของข้อมูลทั้งหมด ส่วน label 1 มีจำนวน 209 rows คิดเป็น 4% ของข้อมูลทั้งหมด จะเห็นว่าสัดส่วนของทั้งสอง label มีความต่างกันมาก ๆ 

## 📝ตารางสรุปผล:

**ตารางที่ 1:** model ที่ใช้ข้อมูลทั้งหมดเลย (Imbalanced)
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 1.1   |    Decision Tree    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)  | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 92% | Class 0: 96%, Class 1: 15% | Class 0: 95%, Class 1: 18%  | Class 0: 96%, Class 1: 16%  | 56%
| 1.2   |   Random Forest    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)  | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 95% | Class 0: 96%, Class 1: 50% | Class 0: 100%, Class 1: 1%  | Class 0: 98%, Class 1: 3%  | 77%
| 1.3   |   XGBoost    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)  | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 95% | Class 0: 96%, Class 1: 25% | Class 0: 99%, Class 1: 6%  | Class 0: 97%, Class 1: 10%  | 77%


**ตารางที่ 2:** model ที่ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 2.1   |    Decision Tree    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling  | 70% = Class 0: 169 rows, Class 1: 165 rows |  30% = Class 0: 44 rows, Class 1: 40 rows | - | 65% | Class 0: 94%, Class 1: 65% | Class 0: 62%, Class 1: 68%  | Class 0: 63%, Class 1: 67%  | 65%
| 2.2   |   Random Forest    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling  |  70% = Class 0: 169 rows, Class 1: 165 rows |  30% = Class 0: 44 rows, Class 1: 40 rows | - | 69% | Class 0: 72%, Class 1: 67% | Class 0: 57%, Class 1: 80%  | Class 0: 64%, Class 1: 73%  | 79%
| 2.3   |   XGBoost    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Under-sampling  |  70% = Class 0: 169 rows, Class 1: 165 rows |  30% = Class 0: 44 rows, Class 1: 40 rows | - | 69% | Class 0: 68%, Class 1: 70% | Class 0: 68%, Class 1: 70%  | Class 0: 68%, Class 1: 70%  | 75%

**ตารางที่ 3:** model ที่ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 3.1   |    Decision Tree    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling |  Class 0: 3762 rows, Class 1: 3762 rows |  Class 0: 937 rows, Class 1: 45 rows | ทำ Over-sampling เฉพาะ train set | 92% | Class 0: 96%, Class 1: 13% | Class 0: 96%, Class 1: 11%  | Class 0: 96%, Class 1: 12%  | 54%
| 3.2   |   Random Forest    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling  |  Class 0: 3762 rows, Class 1: 3762 rows |  Class 0: 937 rows, Class 1: 45 rows | ทำ Over-sampling เฉพาะ train set | 95% | Class 0: 95%, Class 1: 9% | Class 0: 99%, Class 1: 2%  | Class 0: 97%, Class 1: 4%  | 77%
| 3.3   |   XGBoost    |  ใช้ข้อมูลที่เท่ากันด้วยวิธี Over-sampling  |  Class 0: 3762 rows, Class 1: 3762 rows |  Class 0: 937 rows, Class 1: 45 rows | ทำ Over-sampling เฉพาะ train set | 94% | Class 0: 96%, Class 1: 11% | Class 0: 98%, Class 1: 4%  | Class 0: 97%, Class 1: 6%  | 80%


**ตารางที่ 4:** model ที่ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight 
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 4.1   |    Decision Tree    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight   | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 93% | Class 0: 96%, Class 1: 16% | Class 0: 97%, Class 1: 13%  | Class 0: 96%, Class 1: 15%  | 55%
| 4.2   |   Random Forest    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight   | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 95% | Class 0: 96%, Class 1: 33% | Class 0: 100%, Class 1: 1%  | Class 0: 98%, Class 1: 3%  | 77%
| 4.3   |   XGBoost    |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight   | 70% = Class 0: 3293 rows, Class 1: 142 rows |  30% = Class 0: 1406 rows, Class 1: 67 rows | - | 94% | Class 0: 96%, Class 1: 22% | Class 0: 97%, Class 1: 16%  | Class 0: 97%, Class 1: 19%  | 76%


**ตารางที่ 5:** Anomaly Detection ด้วย Auto Encoders  
| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|------:|
| 5.1   |    Anomaly Detection ด้วย Auto Encoders    |  ใช้ข้อมูลทั้งหมดที่เป็นเฉพาะ Class 0 (normal)   | Class 0: 3293 rows |  Class 0: 1406 rows, Class 1: 67 rows | - | 83% | Class 0: 97%, Class 1: 11% | Class 0: 85%, Class 1: 40%  | Class 0: 90%, Class 1: 18%  | 63%

<!-- ตรงนี้ว่าจะเพิ่ม Class 1 ใน test set โดยเอามาจาก train set ที่เป็น Class 1 -->

**ตารางที่ 6:** Anomaly Detection ด้วย IsolationForest
| No. |      Model         |         Dataset            |    Train set & Test set    | Description | Accuracy | Precision | Recall |  F1-Score | AUC |
|-----|:------------------:|---------------------------:|---------:|-----:|-----:|-----:|-----:|------:|------:|
| 6.1   |    Anomaly Detection ด้วย IsolationForest (เป็น unsupervised learning)   |  ใช้ข้อมูลทั้งหมดเลย (Imbalanced)   | ทั้ง Train set และ Test set ใช้ข้อมูลเหมือนกันเลย มี Class 0: 4699 rows, Class 1: 209 rows | ใช้ contamination = 0.05 | 92% | Class 0: 96%, Class 1: 16% | Class 0: 96%, Class 1: 19%  | Class 0: 96%, Class 1: 17%  | 57%

ลองใช้ค่า contamination หลายค่าแล้ว (ดูได้ใน code) ซึ่งค่า 0.05 เป็นค่าที่ได้ค่า Accuracy และ F1-score อยู่ในระดับที่รับได้มากที่สุด 

## 📄สรุป:

จะเห็นว่าหลาย model ยังได้ผลลัพธ์ที่ยังไม่ดีนัก โดยเฉพาะใน class 1 (เป็น Stroke) แม้จะมีการปรับหลาย ๆ อย่างแล้ว ไม่ว่าจะเป็นการทำ Over-sampling, Under-sampling, การปรับ class_weight แล้วก็ตาม 

แต่ถ้าดีที่สุดในที่ทำตอนนี้ ดูจากค่า F1 และค่า AUC ประกอบกัน ก็คงเป็น ตารางที่ 4: XGBoost model ที่ใช้ข้อมูลทั้งหมดเลย (Imbalanced) แต่ปรับ class_weight โดยมีค่า F1 อยู่ที่ Class 0: 97%, Class 1: 19% และค่า AUC 76% 

ซึ่งอาจต้องลองทำ Over-sampling ด้วย SMOTE เพื่อให้ model มีประสิทธิภาพดีมากขึ้น