# Model Card: GRU Activity Recognition Model

## Intended Use

### Primary Use Cases
This model is intended to classify human physical activities using short windows of smartphone inertial sensor data. It should be used for:

- Educational and research purposes (sequence models, time-series classification)  
- Demonstrating GRU-based deep learning models on sensor data  
- Prototyping human activity recognition systems in controlled environments  
- Benchmarking models on the UCI Human Activity Recognition dataset  

The model takes a fixed sensor window of shape **(128, 9)** containing accelerometer and gyroscope signals and predicts one of six activity classes: **WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, or LAYING**.

## Non-Intended Use

This model is **not intended** for:

- Medical diagnosis or rehabilitation monitoring  
- Fall detection or emergency response systems  
- Surveillance or identity inference  
- Monitoring individuals in high-stakes environments such as workplaces or healthcare settings  
- Deployment in environments where device placement or sensor configuration differs significantly from the dataset  

## Evaluation Protocol

The model was evaluated using a **subject-disjoint training/validation/test protocol**. Training and validation splits were created only from the training subjects, and final evaluation was performed on held-out test subjects with no subject overlap.

Performance was assessed using the following metrics:

- **Accuracy:** Overall proportion of correctly classified activity windows  
- **Precision:** Fraction of predicted activity labels that are correct for each class  
- **Recall:** Fraction of actual activity instances correctly identified for each class  
- **F1 Score:** Harmonic mean of precision and recall for each class  
- **Confusion Matrix:** Shows which activities are most frequently confused by the model  

## Known Failure Modes / Limitations

- **Activity Confusion:** Activities with similar motion patterns (e.g., SITTING vs STANDING or related walking activities) may be misclassified.  
- **Fixed Window Size:** The model only processes **128-step windows** and does not incorporate longer-term temporal context.  
- **Device Placement Sensitivity:** Performance may degrade if the smartphone is placed differently than in the dataset.  
- **Sensor Noise Differences:** Real-world sensor readings may vary across devices, affecting performance.  
- **Population Generalization:** The dataset includes a limited number of subjects, so the model may not generalize well to different demographics or movement patterns.

## Privacy / Ethics Note

Although the dataset is anonymized and contains only motion sensor signals rather than audio or video, activity recognition can still reveal patterns about a person’s behavior and daily routines. Any real-world deployment should clearly inform users about what sensor data is collected, minimize retention of raw sensor data, and avoid using predictions for surveillance or punitive decision-making.
