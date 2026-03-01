# 🐶🐱 Dog vs Cat Image Classifier

A Convolutional Neural Network (CNN) built using TensorFlow/Keras to classify images as **Dog** or **Cat**.

---

## 📌 Model Overview

This project implements a binary image classification model using a Sequential CNN architecture.

* **Framework:** TensorFlow / Keras
* **Input Shape:** (100, 100, 3) RGB Images
* **Output:** Binary classification (Dog / Cat)
* **Activation (Final Layer):** Sigmoid

---

## 🧠 Model Architecture

```
Model: "sequential"

Layer (type)                 Output Shape           Param #
=================================================================
conv2d (Conv2D)              (None, 98, 98, 32)        896
max_pooling2d (MaxPooling2D) (None, 49, 49, 32)          0
conv2d_1 (Conv2D)            (None, 47, 47, 32)      9,248
max_pooling2d_1              (None, 23, 23, 32)          0
flatten (Flatten)            (None, 16928)               0
dense (Dense)                (None, 64)           1,083,456
dense_1 (Dense)              (None, 1)                  65
=================================================================
Total params: 3,280,997 (12.52 MB)
Trainable params: 1,093,665 (4.17 MB)
Non-trainable params: 0
Optimizer params: 2,187,332 (8.34 MB)
```

---

## 🔍 Layer Explanation

### 1️⃣ Conv2D (32 filters, 3x3)

* Extracts low-level features (edges, textures)
* Parameters: 896

### 2️⃣ MaxPooling2D (2x2)

* Reduces spatial size
* Prevents overfitting

### 3️⃣ Conv2D (32 filters)

* Learns more complex features (shapes, patterns)
* Parameters: 9,248

### 4️⃣ Flatten

* Converts 2D feature maps into 1D vector

### 5️⃣ Dense (64 neurons)

* Fully connected layer
* Learns classification patterns
* Parameters: 1,083,456

### 6️⃣ Dense (1 neuron, Sigmoid)

* Outputs probability (0 → Dog, 1 → Cat)
* Parameters: 65

---

## 📊 Parameter Breakdown

| Type                 | Count     |
| -------------------- | --------- |
| Total Parameters     | 3,280,997 |
| Trainable Parameters | 1,093,665 |
| Optimizer Parameters | 2,187,332 |
| Model Size           | 12.52 MB  |

Most parameters are in the **Dense layer**, which is common in CNN models.

---

## ⚙️ How to Run

### Install Dependencies

```bash
pip install tensorflow numpy matplotlib pillow
```

### Train Model

```python
model.fit(X_train, Y_train, epochs=10, validation_data=(X_test, Y_test))
```

### Save Model

```python
model.save("dog_cat_model.keras")
```

---

## 🔮 Prediction Example

```python
idx = random.randint(0, len(Y_test))

plt.imshow(X_test[idx])
plt.show()

prediction = model.predict(X_test[idx].reshape(1, 100, 100, 3))

if prediction > 0.5:
    print("Cat 🐱")
else:
    print("Dog 🐶")
```

---

## 📦 Deployment Options

This model can be deployed using:

* FastAPI (Web API)
* Docker Container
* Tkinter Desktop App
* Cloud Deployment (AWS / Azure)

---

## 🚀 Future Improvements

* Add Dropout to reduce overfitting
* Add BatchNormalization
* Increase number of filters
* Use Data Augmentation
* Replace with Transfer Learning (MobileNetV2 / ResNet50)

---

## 📜 License

For educational and research purposes.

