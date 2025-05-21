# Cram-School-Easter-Round-2025
This repository contains my solutions to problems from the Cram School Easter Round 2025. The tasks respect the official format for the Romanian National AI Olympiad (Regional Phase). I achieved a total score of 200/200, Rank 1.

## Cybersecurity AI Challenge
- Subtask 1 - Accuracy: 1
- Subtask 2 - F1 score: 0.8788

In spite of huge investments, cyber attacks have become increasingly sophisticated and frequent. Organizations must analyze vast amounts of network traffic to detect threats early and respond effectively since uncaught vulnerabilities can prove to be ruinous. This challenge simulates a real-world cybersecurity monitoring scenario using a synthetic dataset that represents detailed logs of network activity and behavioral indicators.

The dataset consists of 40,000 records with multiple engineered features that mimic realistic cyber threat detection signals. Each record represents a snapshot of network behavior and system status at a specific moment.

**Dataset Attributes:**
<br>
Each row contains the following fields:

- Timestamp: The date and time of the recorded event
- Suspicious_Port_Activity: Level of abnormality in port usage
- Traffic_Volume_Variation: Deviation in expected traffic volume
- Packet_Length_Anomaly: Variation from normal packet sizes
- Malware_Score: Likelihood of malware presence
- Threat_Level_Index: Estimated severity of threat
- User_Behavior_Score: Behavioral anomaly score for user activity
- Geo_Dispersion: Geographic spread of communication
- Payload_Entropy: Complexity/randomness in packet content
- Login_Attempts: Count of login attempts in the session
- Device_Response_Time: Latency in system's response
- Session_Duration: Duration of user/network session
- Packet_Retry_Rate: Frequency of retransmitted packets
- Anomaly_Tendency: Combined anomaly indicator from multiple subsystems
- Attack Type: Target label, representing the type of detected attack:
  - **0 → DDoS**
  - **1 → Phishing**
  - **2 → Malware**

---

### Subtask 1 – Time of Day Classification
Extract the time of day from the Timestamp from TEST DATASET field and classify each event as either:

- "AM" – events occurring before midday
- "PM" – events occurring after midday

---

### Subtask 2 – Attack Type Prediction
Train a machine learning model to predict the type of cyber attack (Attack Type) based on the other features in the dataset. The goal is to accurately classify each record as one of:

- 0 → DDoS (Distributed Denial of Service)
- 1 → Phishing (Deceptive attempts to steal credentials or sensitive data)
- 2 → Malware (Malicious software attempting unauthorized actions)
  
This task represents a core AI security application: automated attack detection and classification, enabling systems to respond differently based on the threat type.

---

**Notes:**
- For subtask 1, only the Timestamp column is used to derive AM/PM.
- For subtask 2, models are evaluated using F1-score.
- The submission must be a single CSV file containing all predictions for both subtasks.
- The file must follow the exact format: subtaskID, datapointID, answer
- You can download the sample_output.csv provided with the competition files to better understand the required format.



## Brain Anomaly Detection Challenge
- Subtask 1 - Accuracy: 1
- Subtask 2 - 2 x F1_score: 0.6522

**Overview:**
<br>
This competition focuses on the development of a machine learning pipeline for brain anomaly detection using grayscale medical images. The goal is to simulate critical steps in an AI-assisted diagnostic system, particularly those used to preprocess, normalize, and detect abnormalities in neuroimaging data.

Participants will work with a dataset of brain scans and complete two interconnected subtasks:

- Preprocessing via image centering
- Binary classification of anomalies
  
**Dataset:**
<br>
The dataset consists of grayscale PNG images representing 2D brain slices. The images are split into training and test sets. Each training sample is associated with a binary label:

- 0 → Normal brain
- 1 → Abnormal brain (presence of anomaly)
  
Each image is accompanied by a unique identifier (id), and labels are provided only for the training set.

---

### Subtask 1 – Image Normalization
Participants must process each image from the TRAINING SET by applying the following operations:

- The global mean vector must be computed by averaging the pixel values across all training images
- This mean vector must then be subtracted from each individual image vector
- This normalization step is a standard preprocessing technique used in anomaly detection models to highlight structural deviations from the average brain anatomy.

Each submission must return the centered image vectors as numerical arrays.

**Example subtask 1**
<br>
Training dataset:

Image ID	Pixel Vector<br>
img_001	[2, 4, 6, 8]<br>
img_002	[3, 5, 7, 9]<br>
img_003	[1, 3, 5, 7]<br>

**Step 1: Compute global mean vector**
<br>
mean_pixel_1 = (2 + 3 + 1) / 3 = 2.0<br>
mean_pixel_2 = (4 + 5 + 3) / 3 = 4.0<br>
mean_pixel_3 = (6 + 7 + 5) / 3 = 6.0<br>
mean_pixel_4 = (8 + 9 + 7) / 3 = 8.0<br>
<br>
Global mean vector = [2.0, 4.0, 6.0, 8.0]<br>

**Step 2: Subtract the mean from each image**
<br>
Image ID---	Original Pixels ---	Centered Output<br>
img_001	[2, 4, 6, 8]	[0.0, 0.0, 0.0, 0.0]<br>
img_002	[3, 5, 7, 9]	[1.0, 1.0, 1.0, 1.0]<br>
img_003	[1, 3, 5, 7]	[-1.0, -1.0, -1.0, -1.0]<br>

---

### Subtask 2 – Anomaly Classification
Using the labeled training data, participants must train a supervised learning model that can classify unseen test images as either:

- Normal (0)
- Anomalous (1)

---

**Evaluation Criteria:**
- Subtask 1 is evaluated based on correct image processing and format.
- Subtask 2 is scored using the 2 x F1-score, with point thresholds based on performance ranges.
- Submissions must follow the required CSV structure and naming conventions to be considered valid.

**Notes:**
- The submission must be a single CSV file containing all predictions for both subtasks.
- The file must follow the exact format: subtaskID, datapointID, answer
- Submission Format<br>
  subtaskID	---datapointID	--- answer<br>
  1	001	[pixel1, ..., pixelN]<br>
  ...	...	...<br>
  2	101	0<br>
  2	102	1<br>

You can download the sample_output.csv provided with the competition files to better understand the required format.
