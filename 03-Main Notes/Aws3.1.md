  ## 🎯 Exam Essentials

**1. Foundation Model Selection Criteria**

- **Concept:** Select a pre-trained/foundation model based on the application's requirements.
- **Key considerations:** Cost, modality, latency, multilingual support, model size, model complexity, customization, input length, and output length.
- **Exam trigger:** When a question asks _which model should be selected_, look for the requirement that the model must satisfy.

**2. Cost vs. Performance**

- **Concept:** Model selection requires balancing performance against cost.
- **Key distinction:** A more accurate model is not automatically the appropriate choice if its training or operational cost is much higher.
- **Exam trigger:** When two models have different accuracy and costs, evaluate them against the stated business requirements.

**3. Latency and Inference Speed**

- **Concept:** Inference speed is the time required for a model to process input and produce a prediction.
- **Key distinction:** Real-time applications require models whose inference speed satisfies the application's latency constraints.
- **Exam trigger:** Words such as **real-time, instant decisions, latency requirement, response time** should immediately make you consider inference speed.

**4. Model Architecture and Complexity**

- **Concept:** Different architectures have different strengths and weaknesses and should be matched to the task.
- **Examples:** CNN → image recognition; RNN → natural language processing.
- **Key distinction:** Complexity can be associated with parameters, layers, and operations and affects speed, memory, and accuracy.
- **Exam trigger:** When a question describes a particular task and gives multiple architectures, match the architecture to the task requirements.

**5. Modality**

- **Concept:** The required modality is an important criterion when selecting a pre-trained model.
- **Key distinction:** The model must support the type of data required by the application.
- **Exam trigger:** When the question emphasizes a particular type of input/output data, check modality compatibility.

**6. Multilingual Requirements**

- **Concept:** Applications requiring multiple languages need models trained on the relevant languages.
- **Exam trigger:** If a scenario requires support for several specific languages, multilingual capability becomes a model-selection criterion.

**7. Model Performance Evaluation**

- **Concept:** Evaluate a pre-trained model using metrics relevant to the application's task.
- **Metrics mentioned:** Accuracy, precision, recall, F1 score, RMSE, MAP, and MAE.
- **Key distinction:** The appropriate metric depends on the task and dataset characteristics.
- **Exam trigger:** Do not automatically select accuracy; identify what the application is actually measuring.

**8. Object Detection Metrics**

- **Concept:** Object detection evaluates both locating and classifying multiple objects.
- **Key distinction:** The transcript highlights **MAP** as more relevant than overall accuracy for this type of task.
- **Exam trigger:** **Object detection → think MAP.**

**9. Imbalanced Datasets**

- **Concept:** Accuracy may not appropriately represent performance when classes are unevenly distributed.
- **Key distinction:** Consider metrics that better reflect the application's actual performance requirements.
- **Exam trigger:** **Imbalanced dataset → question whether accuracy is appropriate.**

**10. Original Dataset vs. New Dataset**

- **Concept:** A pre-trained model's performance on its original dataset does not by itself establish its suitability for a new application.
- **Key distinction:** Consider performance on both the original and new datasets.
- **Exam trigger:** If a question says the model performed well during original training/testing but is being applied to a new dataset, evaluate its performance on the new data.




---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Foundation model**|Pre-trained model considered for reuse in applications rather than building a model entirely from scratch|
|**Pre-trained model**|Model already trained on an existing dataset that can be evaluated for a new use case|
|**Inference**|Processing data with a trained model to produce a prediction/result|
|**Inference speed**|Duration required for a model to process input and produce a prediction|
|**Latency**|Time constraint associated with obtaining the model's result|
|**Modality**|Type of data handled by the AI system/model|
|**Multilingual model**|Model trained to work with relevant multiple languages|
|**Model complexity**|Complexity associated with factors such as parameters, layers, and operations|
|**Ensemble methods**|Methods that combine multiple models to improve performance|
|**CNN**|Convolutional neural network; transcript associates it with image recognition|
|**RNN**|Recurrent neural network; transcript associates it with natural language processing|
|**MAP**|Mean Average Precision; highlighted for object-detection evaluation|
|**RMSE**|Root Mean Squared Error|
|**MAE**|Mean Absolute Error|
|**F1 score**|Evaluation metric listed among the metrics for comparing models|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Higher-accuracy model vs. lower-cost model**|Requirements involve both performance and budget|Higher accuracy does not automatically justify substantially higher cost|
|**Complex model vs. simpler model**|Choosing an architecture appropriate to the application|Greater complexity can increase resource requirements and affect speed and memory|
|**High-latency vs. low-latency model**|Application has real-time requirements|Real-time applications require inference speed compatible with their latency constraints|
|**Accuracy vs. MAP**|Selecting an evaluation metric|Accuracy measures overall correct predictions; MAP is highlighted for object detection involving locating/classifying multiple objects|
|**Balanced vs. imbalanced dataset**|Selecting performance metrics|Accuracy can be less appropriate when classes are unevenly distributed|
|**Single model vs. ensemble**|Seeking improved model performance|Ensemble methods combine multiple models rather than relying on one model|
|**CNN vs. RNN**|Selecting architecture based on task|Transcript associates CNNs with image recognition and RNNs with NLP|

---

## 🧠 Exam Traps

1. **Trap:** The model with the highest accuracy is always the correct selection.  
    **Correct:** Model selection requires balancing **performance, cost, latency, and other application requirements**.
    
2. **Trap:** A complex model is automatically better for every application.  
    **Correct:** Complexity affects computational resources, memory, speed, and accuracy; architecture must match the use case.
    
3. **Trap:** High model accuracy guarantees that the model will work well for the new application.  
    **Correct:** Consider performance on the **new dataset**, not only the original dataset.
    
4. **Trap:** Inference speed matters only when training the model.  
    **Correct:** Inference speed directly matters when the application has **latency or real-time requirements**.
    
5. **Trap:** Accuracy is always the preferred metric.  
    **Correct:** Metric selection depends on the task and dataset. Accuracy is particularly problematic for **imbalanced datasets**.
    
6. **Trap:** Accuracy is the best metric for object detection simply because it measures correctness.  
    **Correct:** The transcript specifically highlights **MAP** for object detection because it evaluates locating and classifying multiple objects.
    
7. **Trap:** Multilingual requirements can be ignored if the model performs well in its primary language.  
    **Correct:** Choose a model trained on the **languages relevant to the application**.
    
8. **Trap:** Model architecture can be selected independently of the application's task.  
    **Correct:** Different architectures have different strengths and weaknesses and may be more suitable for particular tasks.
    
9. **Trap:** More computationally expensive models are necessarily more appropriate for real-time systems.  
    **Correct:** Real-time systems require inference speed that satisfies their latency constraints.
    
10. **Trap:** The number of parameters is the only measure of model complexity.  
    **Correct:** The transcript identifies **parameters, layers, and operations** as factors affecting complexity.
    
11. **Trap:** A model that performs well on its original dataset automatically satisfies the new application's requirements.  
    **Correct:** Performance should be assessed in relation to the **new dataset/use case** as well.
    

---

# 📝 Exam Questions

### Q1.

A company is selecting a pre-trained model for an image-analysis application. Model A has higher benchmark accuracy but requires substantially more compute resources and has slower inference. Model B has slightly lower accuracy but satisfies the application's latency and budget requirements.

Which consideration should primarily determine the final selection?

**A.** Select Model A because benchmark accuracy should take precedence over operational constraints.  
**B.** Select Model B because model selection should balance performance with cost and latency requirements.  
**C.** Select Model A because greater model complexity guarantees better application performance.  
**D.** Select Model B only if its original training dataset is larger than Model A's.

**Answer: B**

**Why:** The transcript emphasizes balancing **cost, training/inference requirements, performance, and latency** rather than selecting solely by accuracy.

---

### Q2.

An AI application must respond immediately to sensor data. During testing, a candidate model produces highly accurate predictions but takes too long to generate each result.

Which model-selection criterion is most directly violated?

**A.** Multilingual support  
**B.** Modality compatibility  
**C.** Latency constraint  
**D.** Dataset distribution

**Answer: C**

**Why:** Applications requiring real-time results must consider **inference speed and latency**.

---

### Q3.

An organization is evaluating models for detecting multiple objects within photographs. The team initially proposes overall accuracy as the primary evaluation metric.

Which alternative from the transcript is particularly relevant to this use case?

**A.** MAE  
**B.** MAP  
**C.** RMSE  
**D.** Recall

**Answer: B**

**Why:** The transcript specifically highlights **MAP** for object detection because it evaluates how well the model locates and classifies multiple objects.

---

### Q4.

A company needs to deploy a model across applications that process several languages. Two candidate pre-trained models have similar performance on English data, but only one was trained on the languages required by the application.

Which selection criterion is most relevant?

**A.** Number of model layers  
**B.** Multilingual capability  
**C.** Original training cost  
**D.** Number of operations during inference

**Answer: B**

**Why:** The transcript identifies **multilingual support and training on relevant languages** as model-selection considerations.

---

### Q5.

An engineering team observes that one candidate model has substantially more parameters, layers, and operations than another. The team expects this difference to affect memory consumption and inference performance.

Which concept are they evaluating?

**A.** Model modality  
**B.** Model complexity  
**C.** Dataset imbalance  
**D.** Ensemble performance

**Answer: B**

**Why:** Parameters, layers, and operations are identified as factors associated with **model complexity**, which affects speed, memory, and accuracy.

---

### Q6.

A pre-trained model achieves excellent results on the dataset used during its original development. However, the organization's new dataset has different characteristics, and the team wants to determine whether the model is appropriate for deployment.

What should the team consider?

**A.** Only the model's original benchmark performance  
**B.** Only the model's number of parameters  
**C.** Performance on both the original and new datasets  
**D.** Whether the model has the highest possible accuracy

**Answer: C**

**Why:** The transcript explicitly states that performance should be considered on the **original dataset and the new dataset**.

---

### Q7.

A financial organization has a highly imbalanced dataset where one class occurs much more frequently than the other. The team wants a single metric that accurately represents model performance.

Which concern from the transcript should influence their decision?

**A.** Accuracy may not be appropriate for an imbalanced dataset.  
**B.** MAP should always replace accuracy for every classification problem.  
**C.** RMSE should always be used whenever the dataset is imbalanced.  
**D.** Model complexity becomes irrelevant when classes are imbalanced.

**Answer: A**

**Why:** The transcript explicitly warns that **accuracy is not recommended for datasets that are not evenly distributed**.

---

### Q8.

A development team is considering two architectures for an AI application. The application primarily performs image recognition, while another internal application focuses on natural language processing.

Based on the architectural examples in the transcript, which pairing is appropriate?

**A.** CNN for image recognition; RNN for natural language processing  
**B.** RNN for image recognition; CNN for natural language processing  
**C.** CNN for both because image and language tasks require the same architecture  
**D.** RNN for both because recurrent processing is required for all AI applications

**Answer: A**

**Why:** The transcript specifically associates **CNNs with image recognition** and **RNNs with NLP**.

---

### Q9.

A team is deciding between a 98%-accurate model costing hundreds of thousands of dollars to train and a 97%-accurate model costing only a few thousand dollars. Both models satisfy the application's minimum accuracy requirement.

What does the scenario primarily demonstrate?

**A.** Accuracy should always outweigh financial considerations.  
**B.** The least expensive model should always be selected.  
**C.** Model selection requires balancing performance and cost against requirements.  
**D.** The more expensive model must have better inference performance.

**Answer: C**

**Why:** The transcript uses essentially this scenario to illustrate the **cost-versus-performance tradeoff**.

---

### Q10.

An organization combines several models because it expects their combined predictions to provide better performance than relying on any single model.

Which approach does this describe?

**A.** Model compression  
**B.** Ensemble methods  
**C.** Transfer learning  
**D.** Model quantization

**Answer: B**

**Why:** The transcript defines **ensemble methods** as combining several models to achieve better performance than a single model.

---

# ⚡ 30-Second Revision

1. **Foundation-model selection = requirements first**, not simply highest accuracy.
    
2. Evaluate **cost + performance + latency + modality + multilingual needs**.
    
3. **Real-time → inference speed/latency matters.**
    
4. More **parameters/layers/operations → greater model complexity** and resource impact.
    
5. **CNN → image recognition** in this transcript.
    
6. **RNN → NLP** in this transcript.
    
7. Consider performance on **original + new datasets**.
    
8. **MAP → object detection** in the given example.
    
9. **Accuracy can mislead on imbalanced datasets.**
    
10. Metrics mentioned: **accuracy, precision, recall, F1, RMSE, MAP, MAE**.
    
11. **Ensemble = combine multiple models.**
    
12. The correct model is the one that fits the **application's requirements and tradeoffs**, not necessarily the most accurate or most complex model.