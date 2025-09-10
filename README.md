# mini_imggen_numpy_lib

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
pip install -e .
```

**Requirements**:
- Python 3.8+
- NumPy
- Pillow

---

## 🏁 Quickstart

### 1. Train on an image dataset

```python
from mini_imggen_numpy_lib import train_model

train_model(
    data_dir="data/images",   # folder with images
    out_dir="ckpt",           # save directory for model & vocab
    size=32,
    epochs=3,
    batch_size=32,
    lr=0.02,
    log_cb=print
)
```

### 2. Generate an image

```python
from mini_imggen_numpy_lib import generate_image_from_model

output = generate_image_from_model(
    model_dir="ckpt",
    prompt="striped cat",
    out_path="out.png",
    size=32,
    mode="quick"
)
print("Image saved to", output)
```

### 3. Train on text dataset

Prepare a `texts.json` file:
```json
{
  "texts": [
    "the cat sat on the mat",
    "a small striped tiger",
    "a dog chased the ball"
  ]
}
```

Train:
```python
from mini_imggen_numpy_lib import train_text_model

train_text_model(
    dataset_json="texts.json",
    out_dir="ckpt_text",
    epochs=3,
    log_cb=print
)
```

### 4. Generate text

```python
from mini_imggen_numpy_lib import generate_text_from_model

print(generate_text_from_model("ckpt_text", "hello", length=40))
```

---

## 📖 API Overview

- **Text utilities**
  - `tokenize_text(s: str) -> List[str]`
  - `TextVocab` — build, encode, decode, save, load

- **Image utilities**
  - `load_and_preprocess_image(path: str, size: int)`
  - `image_to_tokens(img_arr)` / `tokens_to_image(tokens, size)`

- **Model & Training**
  - `ARBigramText` — toy autoregressive bigram
  - `train_model()` / `generate_image_from_model()`
  - `train_text_model()` / `generate_text_from_model()`

---

## 🔮 Roadmap

- [ ] Top-k / nucleus sampling for text & image
- [ ] Grayscale & multi-channel image support
- [ ] Command-line interface (CLI)
- [ ] Example Jupyter notebooks

---

## 📜 License

MIT License — see [LICENSE](LICENSE) for details.
