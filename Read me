 🚀 Plastic Detection with Distance Calculation & GUI  

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
2️⃣ Run the Script
Save the plastic_detection.py file and execute:

bash
Copy
Edit
python plastic_detection.py
📌 How It Works
1️⃣ Load YOLOv8 AI Model
python
Copy
Edit
from ultralytics import YOLO
model = YOLO("yolov8n.pt")  # Load YOLOv8 AI model
2️⃣ Open the Webcam
python
Copy
Edit
import cv2
cap = cv2.VideoCapture(0)
3️⃣ Distance Calculation
python
Copy
Edit
def calculate_distance(known_width, focal_length, pixel_width):
    return (known_width * focal_length) / pixel_width if pixel_width != 0 else None
4️⃣ Create GUI Window
python
Copy
Edit
import tkinter as tk
root = tk.Tk()
root.title("Plastic Detection")
root.geometry("800x600")
5️⃣ Process Video & Detect Plastic
python
Copy
Edit
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
                filename = f"{SAVE_FOLDER}\\{label}_{time.strftime('%Y%m%d-%H%M%S')}.jpg"
                cv2.imwrite(filename, frame)
6️⃣ Start the GUI
python
Copy
Edit
update_frame()  # Start video loop
root.mainloop()  # Run GUI
🖥 Expected Output
✅ Live webcam feed with detected plastic.
✅ Bounding boxes & distance calculation displayed.
✅ Saved images in C:\Users\tehnic\Desktop\plastic.

⚙️ Customization
1️⃣ Improve Distance Accuracy
Adjust FOCAL_LENGTH after real-world testing.
Use OpenCV calibration tools for precision.
2️⃣ Change Image Save Folder
Modify:

python
Copy
Edit
SAVE_FOLDER = r"C:\Users\tehnic\Desktop\plastic"
to your preferred location.

3️⃣ Add More Plastic Items
Train a custom YOLOv8 model with more plastic categories.
Use Google Colab or LabelImg for dataset preparation.
🔥 Next Steps
🔹 Want a custom AI model for better detection?
🔹 Need to upload detected images to cloud storage (Google Drive, Firebase, AWS)?
🔹 Looking to integrate this with an ESP32-CAM for drones?

Let me know what’s next! 🚀♻️

python
Copy
Edit

---

### **📂 Save This as `README.md`**
You can **save the above content** into a `README.md` file for documentation.  

#### **📌 Save Manually**
1. **Open a text editor** (e.g., Notepad, VS Code).  
2. **Paste the content above**.  
3. **Save as** `"README.md"`.  

#### **📌 Save with Python Script**
If you want Python to generate the file automatically, run this script:

```python
readme_content = """(Paste the full markdown content here)"""

with open("README.md", "w", encoding="utf-8") as f:
    f.write(readme_content)

print("✅ README.md file created successfully!")
