
# 🌿 Plant Disease Detection Using Deep Learning  
### Comparative Study of CNN, VGG16, Deep CNN & MobileNetV2 Models  

---

## 📌 Overview  
Plant diseases significantly impact global crop yields and pose a major threat to sustainable agriculture.  
This project uses **deep learning models** to classify plant leaf diseases using the **PlantVillage dataset**,  
evaluating four architectures:

- **Simple CNN**
- **VGG16 (Transfer Learning)**
- **Deep CNN**
- **MobileNetV2 (Transfer Learning + Fine-tuning)**

This repository includes model code, training pipelines, evaluation results, and a full comparison study.

---

## 🌱 Dataset  
**PlantVillage dataset (38 classes)**  
🔗 https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset  

Includes healthy and diseased leaf images from crops such as:  
Apple, Tomato, Cotton, Corn, Pepper, Potato, Soybean, Raspberry, and more.

All images are resized to **128×128 pixels**.

---

## 🛠️ Preprocessing  
### ✔ Image Resizing  
All images resized to **128×128**.

### ✔ Dataset Split  
- 80% Training  
- 20% Validation/Test  

### ✔ Data Augmentation  
- Random Rotation  
- Random Horizontal Flip  
- Random Vertical Flip  
- Random Zoom  

---

## 🧠 Model Architectures  

Below are simplified architecture diagrams in GitHub-friendly ASCII format.

---

## 1️⃣ Simple CNN

```
Input (128x128x3)
│
├── Rescaling
│
├── Conv2D (16 filters) → ReLU
│   └── MaxPooling2D
│
├── Conv2D (32 filters) → ReLU
│   └── MaxPooling2D
│
├── Conv2D (64 filters) → ReLU
│   └── MaxPooling2D
│
├── Flatten
├── Dense (128) → ReLU
└── Dense (38) → Softmax
```

**Accuracy:** 90.85%

---

## 2️⃣ VGG16 (Transfer Learning)

```
Input (128x128x3)
│
├── Rescaling
├── Data Augmentation
│
├── VGG16 Base (Frozen)
│   └── Pretrained ImageNet Convolutions
│
├── Flatten
├── Dense (256) → ReLU
├── Dropout (0.5)
└── Dense (38) → Softmax
```

**Accuracy:** 87.09%

---

## 3️⃣ Deep CNN

```
Input (128x128x3)
│
├── Block 1:
│   ├── Conv2D (32) + BN → ReLU
│   ├── Conv2D (32) + BN → ReLU
│   └── MaxPooling2D
│
├── Block 2:
│   ├── Conv2D (64) + BN → ReLU
│   ├── Conv2D (64) + BN → ReLU
│   └── MaxPooling2D
│
├── Block 3:
│   ├── Conv2D (128) + BN → ReLU
│   ├── Conv2D (128) + BN → ReLU
│   └── MaxPooling2D
│
├── Block 4:
│   ├── Conv2D (256) + BN → ReLU
│   ├── Conv2D (256) + BN → ReLU
│   └── MaxPooling2D
│
├── Flatten
├── Dense (512) → ReLU
├── Dropout (0.5)
└── Dense (38) → Softmax
```

**Accuracy:** 95.41%

---

## 4️⃣ MobileNetV2 (Transfer Learning + Fine-tuning)

```
Input (128x128x3)
│
├── Data Augmentation
├── Rescaling
│
├── MobileNetV2 Base (Frozen initially)
│   └── Depthwise Separable Convolutions
│
├── GlobalAveragePooling2D
├── Dense (128) → ReLU
├── Dropout (0.3)
└── Dense (38) → Softmax
```

Training Strategy:  
- Phase 1: train top classifier  
- Phase 2: unfreeze last 30 layers and fine-tune  

**Accuracy:** 96.46% (Best)

---

## 📊 Model Comparison

| Model | Test Accuracy | Notes |
|-------|--------------|-------|
| Simple CNN | 90.85% | Light baseline model |
| VGG16 | 87.09% | Underperformed due to limited tuning |
| Deep CNN | 95.41% | Strong extraction of deep features |
| **MobileNetV2** | **96.46%** | ⭐ Best-performing model |

---

## 🏆 Best Model  
### **🥇 MobileNetV2 – 96.46% Accuracy**  
Reasons:
- Efficient + accurate  
- Excellent generalization  
- Transfer learning + fine-tuning boosts performance  
- Low computational cost → great for mobile deployment  

---

## 🚀 How to Run

Clone repo:
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```
Run notebooks:
```bash
jupyter notebook
```

---

## 📦 Technologies Used
- Python  
- TensorFlow / Keras  
- NumPy / Pandas  
- Matplotlib  
- Jupyter / Colab  
- Transfer Learning architectures (VGG16, MobileNetV2)

---

## 👨‍🏫 Contributors
- IT22076052 – Mahindarathna D.G.P.T.D  
- IT22060662 – Jameela M.J.F  
- IT22011398 – Kariyawasam M.G.P.Y  
- IT22032324 – Gunawickrama I.U.S.U.G  

---

## 📄 License  
This project is for academic and research purposes.

