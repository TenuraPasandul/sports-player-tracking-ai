# Sports Player Tracking AI

This project focuses on **detecting players in sports videos** using **YOLOv8** models as part of the *DS5216 - Artificial Intelligence (2024/25)* coursework.  
It demonstrates how computer vision and deep learning can be applied to automate **player detection** in dynamic sports scenes such as cricket, rugby, handball, and dodgeball.

---

## Project Overview
This work implements a **YOLO-like object detection framework** for identifying players in short sports video clips.  
Keypoint detection was optional and not included to focus on the core detection task.

Two pre-trained models from **Ultralytics YOLOv8** (`YOLOv8n` and `YOLOv8m`) were evaluated to compare their performance in accuracy and efficiency.  
Both models detect the **‘person’** class from the **COCO dataset**, which aligns with player detection needs.

---

## Methodology

### Dataset
Five short video clips (5–10 seconds each) were collected from YouTube:
- **sports_1.mp4** – Dodgeball  
- **sports_2.mp4** – Cricket  
- **sports_3.mp4** – Rugby  
- **sports_4.mp4** – Rugby  
- **sports_5.mp4** – Handball  

Frames from these clips were extracted and analyzed using **OpenCV** and **PyTorch**.

### Model Details
- **Framework:** PyTorch  
- **Models Used:** YOLOv8n, YOLOv8m (pre-trained on COCO dataset)  
- **Detection Class:** `person`  
- **Confidence Threshold:** 0.5  
- **Visualization:** Matplotlib  

No fine-tuning was performed due to the lack of annotated ground-truth data.

---

## Results

### COCO Benchmark Metrics
| Model | mAP@50–95 | Parameters | FLOPs | Inference Speed (A100) |
|--------|------------|-------------|--------|------------------------|
| YOLOv8n | 37.3 | 3.2M | 8.7B | 0.99 ms |
| YOLOv8m | 50.2 | 25.9M | 78.9B | 1.83 ms |

**Observation:**  
- YOLOv8m achieved higher accuracy, while YOLOv8n was faster and more lightweight.  
- Average detections per frame were higher with YOLOv8m (4–6 players) than YOLOv8n (3–5 players).  

---

## Visual Results
Example visualizations include:
- **Dodgeball:** High detection counts early, with confidence peaks around 0.9  
- **Cricket:** Consistent detections, confidence around 0.9  
- **Rugby:** Fluctuating detections due to motion and occlusions  
- **Handball:** Gradual detection decrease, confidence near 0.9  

---

## Discussion

### Model Performance
- **YOLOv8m** demonstrated better accuracy but required higher computational resources.  
- **YOLOv8n** was faster, ideal for real-time applications on limited hardware.  

### Limitations
- No ground-truth annotations (no direct precision/recall computation).  
- Pre-trained model might misdetect referees or bystanders.  
- No temporal tracking (players not tracked across frames).  
- Motion blur and occlusion reduce accuracy.

### Future Improvements
- Annotate videos for fine-tuning and generate loss curves.  
- Add **tracking** (e.g., ByteTrack) for consistent player IDs.  
- Incorporate **keypoint detection** using YOLOv8-pose.  
- Use **data augmentation** for better generalization.  
- Experiment with **ensemble models** for balanced performance.



## 🔗 Useful Links
- **GitHub Repository:** [sports-player-tracking-ai](https://github.com/TenuraPasandul/sports-player-tracking-ai.git)  
- **Google Colab Notebook:** [Open in Colab](https://colab.research.google.com/drive/1mx35MUCNGdWxDlY6j7ZpQFqCvSL-B-AH?usp=sharing)

---

## Author
**K.G.T.P. Gamage**  
M.Sc. in Data Science and Artificial Intelligence  
Postgraduate Institute of Science, University of Peradeniya
