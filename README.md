# Tactical Formation Recognizer ⚽

A  project that reads **broadcast football images**, detects players using **YOLOv8n**, groups them into **two teams by jersey colour**, and estimates each team’s **formation** (e.g. `4-4-2`, `3-5-2`) and **role** (attacking vs defending). The output is an **annotated image** plus a short **tactical summary** for every frame.

## 1. Features

- Detects players (class `person`) using **YOLOv8n**.
- Splits players into **two teams** using jersey colour (HSV + KMeans).
- Estimates team formations by clustering players into **defence–midfield–attack** lines.
- Labels which team is **attacking** and which is **defending** based on vertical depth.
- Visualises everything on top of the original image.

---

## 2. Folder Structure (Recommended)

You don’t have to follow this exactly, but it’s a good default:

TacticalFormationRecognizer/  
├─ ak5455_Project.ipynb        # Main notebook  
├─ README.md
├─ images/                     # Input broadcast frames  
│   ├─ frame1.png  
│   ├─ frame2.jpg  
│   └─ ...  


> You will need to update the paths in the notebook to match where **your** `images/` and `outputs/` folders are.

---

## 3. Dependencies

### Core Python Packages

These are the main libraries used in the notebook:

- `ultralytics` – YOLOv8 model
- `opencv-python` – image I/O and drawing (`cv2`)
- `numpy` – numerical operations
- `scikit-learn` – `KMeans` for clustering
- `matplotlib` – optional, for simple plots
- `google.colab` – only when running in Colab (for `cv2_imshow`, Drive mounting, etc.)

Example `requirements.txt` (for local use):

ultralytics  
opencv-python  
numpy  
scikit-learn  
matplotlib  

In **Google Colab**, most things are preinstalled. You usually only need:

`!pip install ultralytics scikit-learn`

---

## 4. How to Run in Google Colab (Recommended)

### Step 1 – Put files in Google Drive

1. Create a folder in Drive, e.g.  
   `MyDrive/TacticalFormationRecognizer/`
2. Inside it, place:
   - `ak5455(FINAL_PROJECT).ipynb`
   - an `images/` folder with your input frames (e.g. screenshots from matches)

Example Drive layout:

MyDrive/  
└─ TacticalFormationRecognizer/  
&nbsp;&nbsp;&nbsp;&nbsp;├─ ak5455_Project.ipynb  
&nbsp;&nbsp;&nbsp;&nbsp;└─ images/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ frame1.png  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ frame2.png  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ ...

### Step 2 – Open the notebook in Colab

- Go to https://colab.research.google.com
- `File → Open notebook → Google Drive →` select `ak5455(FINAL_PROJECT).ipynb`.

### Step 3 – Mount Google Drive

In the first cell of the notebook (or add a new one), run:

```python
from google.colab import drive
drive.mount('/content/drive')
