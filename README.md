# Yu-Gi-Oh Card Classification Model
**Model file:** `efficientnet_b0_yugioh_finetuned.pth`  
**Framework:** PyTorch  
**Base Architecture:** EfficientNet-B0 (Fine-tuned)

---

## 📌 Overview
This model is a fine-tuned version of **EfficientNet-B0**, trained to classify **Yu-Gi-Oh! trading cards** based on their artwork.  
It predicts the most likely card names given a single card image input.

- **Total Classes:** **13,608 cards** (check `classes.json` for details)  
- **Input Resolution:** `224 x 224` pixels (RGB)  
- **Output:** Top-5 predicted card names with probabilities  
- **TTA Support:** ✅ When **Test-Time Augmentation (TTA)** is enabled, the model achieves **higher prediction stability and accuracy**, especially for visually similar cards.

---

## 📦 Files
- **`efficientnet_b0_yugioh_finetuned.pth`**  
  The trained model weights.

- **`classes.json`**  
  A list of supported card classes with corresponding image filenames:

  ```json
  [
    {
      "name": "Apophis the Swamp Deity",
      "image": "Apophis the Swamp Deity.jpg"
    },
    {
      "name": "Sonic Stun",
      "image": "Sonic Stun.jpg"
    }
  ]
  ```

- **`static/cards/`**  
  Folder containing card reference images used for UI display.

---

## ✅ Requirements

```bash
pip install torch torchvision pillow flask
```

---

## ✅ Example Output

```python
[
  {
    'name': 'Apophis the Swamp Deity',
    'prob': 96.27,
    'image': '/static/cards/Apophis the Swamp Deity.jpg'
  },
  {
    'name': 'Sonic Stun',
    'prob': 2.12,
    'image': '/static/cards/Sonic Stun.jpg'
  }
]
```

---

## 🌐 Web

[http://wisel.bot.nu/](http://wisel.bot.nu/)

---

## 📝 Model Details

- **Base Model:** EfficientNet-B0  
- **Pretrained on:** ImageNet  
- **Fine-tuning Dataset:** *Yu-Gi-Oh! card artworks* (cropped, augmented)  
- **Augmentations:**
  - RandomHorizontalFlip
  - RandomRotation (±10°)
  - ColorJitter (brightness, contrast, saturation, hue)
- **TTA (Test-Time Augmentation):**  
  - Random horizontal flips and rotations applied during inference  
  - Improves prediction consistency and accuracy for similar artworks

---

## 📊 Accuracy (TTA vs Non-TTA)

| Metric            | Without TTA | With TTA (5 rounds) |
|--------------------|-------------|---------------------|
| **Top-1 Accuracy** | ~89.3%      | **~91.7%**          |
| **Top-5 Accuracy** | ~97.8%      | **~98.6%**          |

✅ **TTA improves stability and accuracy**, especially for visually similar or low-quality card scans.

---

## ⚠️ Disclaimer
This model is trained for **educational and fan-use purposes only** and is **not affiliated with Konami or Yu-Gi-Oh!**  
Some cards may be misclassified due to artwork similarities.

---

## 📜 License
This project is for **non-commercial use only**.  
Please respect the official Yu-Gi-Oh! copyrights when using this model.
