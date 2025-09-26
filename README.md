# Gloved-vs-Ungloved-Hand-Detection

# Gloved vs Bare Hand Detection

This project detects whether a hand is **gloved** or **bare** using YOLOv8.

---

## Dataset

- **Name:** Sample Hand Images  
- **Source:** Collected manually from free image sources (Unsplash, Pexels, Google Images)  
- **Contents:**  
  - Gloved hands  
  - Bare hands  
- **Notes:** Small sample dataset for testing the detection script. For proper training, a larger labeled dataset is recommended.

---

## Model

- **YOLOv8** (`yolov8n.pt`) pre-trained on COCO dataset  
- **Custom Training:** None for now (using pre-trained weights)  
- **Classes:**  
  - Simulation: `gloved_hand`, `bare_hand` (for testing purposes)  

> Future work: Train YOLOv8 on a labeled gloved vs bare hand dataset for real detection.

---

## Preprocessing / Training

- **Preprocessing:**  
  - Images resized automatically by YOLO during inference  
  - Only image files (`.jpg`, `.jpeg`, `.png`) are processed  
- **Training:**  
  - None yet; using pre-trained YOLOv8n for demo  
  - Simulated gloved/bare classification in the script for testing  

---

## What Worked

- Detects **person objects** in images using pre-trained YOLOv8  
- Annotated images are saved in `./output` folder  
- JSON logs per image and a combined log in `./logs`  
- Compatible with multiple image formats  

---

## What Didn’t Work

- Pre-trained YOLOv8 cannot detect **gloved vs bare hands** accurately  
- Overwriting `model.names` with custom 2 classes on pre-trained YOLO causes `KeyError`  
- Needs a **custom-trained YOLO model** on gloved/bare hand dataset for real detection  

---

## How to Run

1. Clone or download this repository.  
2. Prepare an image folder, e.g., `sample_images/`, with `.jpg` or `.png` images.  
3. Ensure you have **YOLOv8 installed**:

```bash
pip install ultralytics opencv-python
Run the detection script:

bash
Copy code
python detect.py
Enter paths when prompted:

pgsql
Copy code
Enter path to image folder (e.g., ./sample_images): ./sample_images
Enter YOLO model path (.pt, e.g., yolov8n.pt): yolov8n.pt
Results:

Annotated images → ./output/

JSON logs → ./logs/

Combined log → ./logs/all_detections.json
