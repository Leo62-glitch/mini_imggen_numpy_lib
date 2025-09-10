# mini_imggen_numpy_lib

THE PROJECT IS NOT FINISHED, PLEASE WAIT A FEW HOURS

A lightweight educational Python library for toy **image & text generation** using **NumPy only**. This project is a refactored version of a Tkinter-based demo, now provided as a clean, reusable library without GUI dependencies.

⚠️ **Note**: This is a **toy project** — it is not designed for production use. The models are extremely simple and intended for experimentation, learning, and fun.

---

## ✨ Features

- 🔡 **Text Vocabulary**: Tokenization, vocabulary building, encoding/decoding, save/load.
- 🖼️ **Image Handling**: Load, resize, preprocess, and map images into token sequences.
- 🤖 **Autoregressive Model**: Minimal bigram model for both images and text with optional conditioning.
- 📚 **Dataset Utilities**: Build datasets from image folders or JSON text files.
- 🏋️ **Training**: Simple SGD training loops for images and text.
- 🎨 **Generation**:
  - Generate toy images conditioned on text prompts.
  - Generate text sequences with a trained model.
- 💾 **Persistence**: Save/load models (`.npz`) and vocabularies (`.json`).

---

## 🚀 Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/your-username/mini_imggen_numpy_lib.git
cd mini_imggen_numpy_lib
pip install .
```

**Requirements**:
- Python 3.8+
- NumPy
- Pillow

---

## 🏁 Usage Examples

### Train on a folder of images (filenames are used as text prompts)
```python
from mini_imggen_numpy_lib import train_model

train_model(
    'data/images',   # folder containing images
    'ckpt',          # output directory for model and vocab
    size=32,
    epochs=3,
    batch_size=32,
    lr=0.02,
    log_cb=lambda s: print(s)
)
```

### Generate an image from a trained model
```python
from mini_imggen_numpy_lib import generate_image_from_model

generate_image_from_model(
    'ckpt',
    'striped cat',
    'out.png',
    size=32,
    mode='quick'
)
```

### Train a text model from JSON `{ "texts": ["a sentence", ...] }`
```python
from mini_imggen_numpy_lib import train_text_model

train_text_model(
    'texts.json',
    'ckpt_text',
    epochs=3,
    log_cb=print
)
```

### Generate text
```python
from mini_imggen_numpy_lib import generate_text_from_model

print(generate_text_from_model('ckpt_text', 'hello', length=40))
```

---

## 🔮 Roadmap

- [ ] Top-k / nucleus sampling for text & image
- [ ] Grayscale & multi-channel image support
- [ ] Command-line interface (CLI)
- [ ] Example Jupyter notebooks

---

## 📜 License

MIT License — see [LICENSE](LICENSE) for details.
