# Yellow-detection
# 🌿 Yellow Shade-Based Plant Disease Detection using OpenCV

This project uses a webcam feed and computer vision techniques to detect and classify possible plant diseases based on **yellow coloration** in leaves. It identifies potential **Nitrogen Deficiency**, **Fungal Infection**, or **Potassium Deficiency** by analyzing the HSV color values from the live camera input.

---

## 📸 Features

- Real-time plant leaf monitoring using a webcam.
- HSV color threshold tuning with interactive trackbars.
- Disease classification based on yellow shade analysis:
  - **Light Yellow** → Nitrogen Deficiency
  - **Dark Yellow** → Fungal Infection
  - **Bright Yellow** → Potassium Deficiency
- Image enhancement using CLAHE for better detection in low-light conditions.
- Morphological operations to improve mask quality.
- Visual feedback: bounding boxes, color values, and disease label overlayed on detected regions.

---

## 🛠️ Requirements

- Python 3.x
- OpenCV (`cv2`)
- NumPy

Install dependencies using pip:

```bash
pip install opencv-python numpy
```

---

## 🚀 How to Run

1. **Connect a webcam** to your system.
2. Save the script to a file (e.g., `detect_plant_disease.py`).
3. Run the script:

```bash
python detect_plant_disease.py
```

4. A window with trackbars will appear:
   - Adjust **HSV thresholds** to isolate yellow regions on leaves.
   - Use the **Brightness** slider for better lighting.
   - Use **MinArea** to filter out small noise-like contours.

---

## 🎛️ Trackbar Controls

| Trackbar     | Purpose                        |
|--------------|--------------------------------|
| H_min / H_max| Hue range for yellow color     |
| S_min / S_max| Saturation range               |
| V_min / V_max| Brightness (value) range       |
| MinArea      | Minimum contour area to detect |
| Brightness   | Adjusts brightness of the input|

---

## 🧠 Disease Detection Logic

Based on average HSV values of detected yellow regions:

| Condition                              | Disease Detected              |
|----------------------------------------|-------------------------------|
| `v > 180 and s < 100`                  | Nitrogen Deficiency (Light)   |
| `s > 150 and v < 180`                  | Fungal Infection (Dark)       |
| `s > 100 and v > 180`                  | Potassium Deficiency (Bright)|
| Else                                   | Unknown yellow shade          |

---

## 📷 Output Windows

- **Original**: Raw webcam feed
- **Enhanced**: CLAHE-enhanced frame with detected disease annotations
- **Mask**: Binary mask of yellow regions based on HSV thresholds

---

## 🛑 Exit

- Press **`q`** key to quit the application.

---

## 📌 Notes

- Ensure good lighting for better accuracy.
- You may need to fine-tune HSV values for different leaf types or lighting environments.
- The model does **not** use machine learning—it is based on simple HSV color range classification.

---

## 🔖 License

This project is open-source and free to use under the MIT License.
