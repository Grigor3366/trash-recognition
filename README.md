# 🚀 Plastic Detection with Distance Calculation & GUI  

## 📖 Overview  
This Python script detects **plastic waste (bottles, cups, plastic bags)** using **YOLOv8 AI**.  
✅ **Calculates distance** to detected plastic.  
✅ **Saves detected images** to `C:\Users\tehnic\Desktop\plastic`.  
✅ **Displays an interactive GUI** with object info.  

---

## 🛠 Installation & Setup  
### **1️⃣ Install Required Libraries**  
Run the following command:  
```bash
pip install opencv-python numpy ultralytics pillow
```

### **2️⃣ Run the Script**  
Save the `plastic_detection.py` file and execute:  
```bash
python plastic_detection.py
```

---

## 📌 How It Works  
### **1️⃣ Load YOLOv8 AI Model**
```python
from ultralytics import YOLO
model = YOLO("yolov8n.pt")  # Load YOLOv8 AI model
```

### **2️⃣ Open the Webcam**
```python
import cv2
cap = cv2.VideoCapture(0)
```

### **3️⃣ Distance Calculation**
```python
def calculate_distance(known_width, focal_length, pixel_width):
    return (known_width * focal_length) / pixel_width if pixel_width != 0 else None
```

### **4️⃣ Create GUI Window**
```python
import tkinter as tk
root = tk.Tk()
root.title("Plastic Detection")
root.geometry("800x600")
```

### **5️⃣ Process Video & Detect Plastic**
```python
def update_frame():
    ret, frame = cap.read()
    results = model(frame)

    for result in results:
        for box in result.boxes:
            x1, y1, x2, y2 = map(int, box.xyxy[0])
            label = result.names[int(box.cls[0])]
            confidence = box.conf[0]

            if label in ["bottle", "cup", "plastic bag"]:
                distance = calculate_distance(KNOWN_WIDTH, FOCAL_LENGTH, x2 - x1)
                filename = f"{SAVE_FOLDER}\{label}_{time.strftime('%Y%m%d-%H%M%S')}.jpg"
                cv2.imwrite(filename, frame)
```

### **6️⃣ Start the GUI**
```python
update_frame()  # Start video loop
root.mainloop()  # Run GUI
```

---

## 🖥 Expected Output  
✅ **Live webcam feed** with detected plastic.  
✅ **Bounding boxes** & **distance calculation** displayed.  
✅ **Saved images** in `C:\Users\tehnic\Desktop\plastic`.  

---

## ⚙️ Customization  
### **1️⃣ Improve Distance Accuracy**
- Adjust **FOCAL_LENGTH** after real-world testing.  
- Use **OpenCV calibration tools** for precision.  

### **2️⃣ Change Image Save Folder**
Modify:
```python
SAVE_FOLDER = r"C:\Users\tehnic\Desktop\plastic"
```
to your preferred location.  

### **3️⃣ Add More Plastic Items**
- Train a **custom YOLOv8 model** with more plastic categories.  
- Use **Google Colab** or **LabelImg** for dataset preparation.  

---

## 🔥 Next Steps  
🔹 **Want a custom AI model for better detection?**  
🔹 **Need to upload detected images to cloud storage (Google Drive, Firebase, AWS)?**  
🔹 **Looking to integrate this with an ESP32-CAM for drones?**  

Let me know what’s next! 🚀♻️  
