🏥 CURASCAN — INTELLIGENT HEALTH CARE IMAGING
CURASCAN is a Streamlit-based medical imaging platform with AI-powered classification and segmentation. It supports chest X-ray pneumonia detection, MRI brain tumor ("Glioma", "Meningioma", "No Tumor", "Pituitary") classification, and CT scan segmentation.

Project Structure
CURASCAN/
│
├── models/
│   ├── densenet_classifier.py
│   ├── unet_segmenter.py
│   └── gradcam_utils.py
│
|
|── data/
|    ├── xray/
|    │    ├── train/
|    |    |      ├──normal
|    |    |      ├──penumonia
|    │    ├── test/
|    |    |      ├──normal
|    |    |      ├──penumonia
|    │    └── val
|    |         ├──normal
|    |         ├──penumonia
|    ├── mri/
|    │      ├── test/
|    |      |      └──glioma
|    |      |      └──meningioma
|    |      |      └──notumor
|    |      |      └──pituitary
|    │      ├── train/
|    |          └──glioma
|    |          └──meningioma
|    |          └──notumor
|    |          └──pituitary
|    │   
|    └── ct/
|         ├── train/
|         |      ├──normal
|         |      ├──penumonia
|         ├── test/
|         |      ├──normal
|         |      ├──penumonia
|         └── val/
|               ├──normal
|               ├──penumonia

├── train/
│   ├── train_classification.py
│   ├── train_segmentation.py
│   └── kfold_training.py
│
├── app/                 
│   ├── app.py            # Streamlit apps 
│
├── utils/
│   ├── datasets.py
│   ├── losses.py
│   ├── metrics.py
│   └── augmentations.py
│
├── scans/                # Uploaded patient scans (runtime)
├── checkpoints/          # Saved model weights (runtime)
├──config.py
├──reports_utils.py
├──database.py
├── curascan.db           # SQLite database (runtime)
├── requirements.txt
├── README.md

---

## Quick Start

### 1. Install dependencies

```bash
pip install -r requirements.txt
2. (Optional) Train models
# Classification (chest X-ray)
./run.sh train cls --task xray --epochs 30

# Segmentation (CT)
./run.sh train seg --epochs 50

# K-Fold cross-validation
./run.sh train kfold --task xray --k 5
Repeat for MRI & CT Trained checkpoints are saved to checkpoints/cls_best.pth and checkpoints/seg_best.pth.

3. Run the apps
streamlit run app/app.py

Default admin credentials: admin / admin123
