# 📡 Satellite Image Data Analysis using NumPy

## 📌 Project Overview

This project demonstrates how to analyze **satellite image data** using **NumPy and Python**.
The dataset is derived from the **WIFIRE (Wildfire Integrated Framework for Information and Response)** system, which is used for wildfire prediction and environmental monitoring.

The goal is to understand how image data can be treated as numerical arrays and processed for **scientific analysis and machine learning applications**.

---

## 🌍 About WIFIRE

WIFIRE is an advanced system that integrates:

* Satellite imagery
* Real-time sensor data
* Weather patterns
* Computational models

It helps in predicting wildfire spread and analyzing environmental conditions.

---

## 🎨 RGB Mapping in Dataset

Each satellite image uses RGB channels to represent real-world features:

| Channel  | Meaning  |
| -------- | -------- |
| 🔴 Red   | Altitude |
| 🟢 Green | Slope    |
| 🔵 Blue  | Aspect   |

👉 Higher pixel values = Higher intensity (e.g., higher altitude, slope, etc.)

---

## 🛠️ Technologies Used

* Python 🐍
* NumPy
* Matplotlib
* ImageIO
* SciPy
* Scikit-Image

---

## 📂 Project Structure

```
📁 Satellite-Image-Analysis
│
├── data/
│   └── sd-3layers.jpg
│
├── notebook / script
│   └── analysis.py / .ipynb
│
└── README.md
```

---

## 🚀 Key Features & Operations

### 1️⃣ Image Loading & Conversion

* Load image using `imageio`
* Convert into NumPy array

```python
photo_data = imageio.imread('data/sd-3layers.jpg')
```

---

### 2️⃣ Basic Image Analysis

* Shape, size, min, max, mean
* Pixel-level inspection

```python
print(photo_data.shape)
print(photo_data.min(), photo_data.max())
print(photo_data.mean())
```

---

### 3️⃣ Pixel Manipulation

* Modify individual pixels
* Change RGB values

```python
photo_data[150, 250] = [255, 0, 0]
```

---

### 4️⃣ Region-Based Editing

* Modify ranges of rows/columns

```python
photo_data[200:800, :, 1] = 255
```

---

### 5️⃣ Filtering & Masking

* Remove low-value pixels
* Apply logical conditions

```python
low_value_filter = photo_data < 100
photo_data[low_value_filter] = 0
```

---

### 6️⃣ Pattern Creation

* Create diagonal patterns using indexing

```python
rows = np.arange(len(photo_data))
photo_data[rows, rows] = 255
```

---

### 7️⃣ Circular Masking

* Apply geometric masks

```python
dist = (X - center_row)**2 + (Y - center_col)**2
mask = dist > radius
photo_data[mask] = 0
```

---

### 8️⃣ Feature Extraction (Scientific Insight)

#### 🔴 High Altitude Detection

```python
red_mask = photo_data[:, :, 0] < 150
photo_data[red_mask] = 0
```

#### 🟢 High Slope Detection

```python
green_mask = photo_data[:, :, 1] < 150
photo_data[green_mask] = 0
```

#### 🔵 High Aspect Detection

```python
blue_mask = photo_data[:, :, 2] < 150
photo_data[blue_mask] = 0
```

---

### 9️⃣ Composite Filtering

Combine multiple conditions:

```python
final_mask = np.logical_and(red_mask, green_mask, blue_mask)
photo_data[final_mask] = 0
```

---

## 📊 Output Visualization

All transformations are visualized using:

```python
plt.imshow(photo_data)
plt.show()
```

---

## 💡 Learning Outcomes

* Understand image as NumPy arrays
* Perform pixel-level operations
* Apply masking and filtering techniques
* Extract meaningful insights from image data
* Build foundation for Computer Vision & ML

---

## 🔥 Real-World Applications

* Wildfire prediction
* Terrain analysis
* Environmental monitoring
* Remote sensing
* GIS systems

---

## ▶️ How to Run

1. Install dependencies:

```bash
pip install numpy matplotlib imageio scipy scikit-image
```

2. Run script:

```bash
python analysis.py
```

---

## 📎 Future Improvements

* Apply Machine Learning on extracted features
* Integrate with Power BI dashboard
* Automate wildfire risk detection
* Use deep learning (CNN) for image classification

---

## 🙌 Author

**Viral Parmar**
Logistics & Data Enthusiast | Python | Power BI | ML

---

## ⭐ Support

If you found this project useful:

* ⭐ Star the repo
* 🍴 Fork it
* 📢 Share it

---
