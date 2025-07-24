# Yu-Gi-Oh Card Classification Model
**Model file:** `efficientnet_yugioh_finetuned_game.pth`  
**Framework:** PyTorch  
**Base Architecture:** EfficientNet-B0 (Fine-tuned)

---

## 📌 Overview
This model is a fine-tuned version of **EfficientNet-B0**, trained to classify **Yu-Gi-Oh! trading cards** based on their artwork.  
It predicts the most likely card names given a single card image input.

- **Total Classes:**  *N* cards (check `classes.json` for details)  
- **Input Resolution:** `224 x 224` pixels (RGB)  
- **Output:** Top-5 predicted card names with probabilities

---

## 📦 Files
- **`efficientnet_yugioh_finetuned_game.pth`**  
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

## Requirements
```bash
pip install torch torchvision pillow flask
```

---

## Example Output
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

---

## ⚠️ Disclaimer
This model is trained for **educational and fan-use purposes only** and is **not affiliated with Konami or Yu-Gi-Oh!**  
Some cards may be misclassified due to artwork similarities.

---

## 📜 License
This project is for **non-commercial use only**.  
Please respect the official Yu-Gi-Oh! copyrights when using this model.
