# Fooocus Custom Colab & Local Setup Framework

An optimized deployment framework and launcher script for **Fooocus** (SDXL-based image generation engine). Designed for Google Colab with Google Drive storage persistence, custom checkpoint presets, and automated source fixes.

---

## Key Features & Modifications

* **Google Drive Persistence:** Downloaded `.safetensors` models, LoRAs, and generated images persist in Google Drive across Colab session resets.
* **`no_init_weights` Fix:** Automates an inline hotfix in `modules/patch_clip.py` to prevent execution crashes with recent PyTorch/Transformers releases.
* **Preset Override:** Configures `talmendoxlSDXL_v11Beta.safetensors` as the default base model inside `presets/default.json`.
* **High-VRAM Optimization:** Uses `--always-high-vram` and `--share` flags for optimal generation speeds and direct Gradio URL tunneling.

---

## 1. Google Colab Setup (Cloud)

1. Open `fooocus_colab.ipynb` directly in Google Colab.
2. Run the code cell.
3. Authorize Google Drive access when prompted on the first run.
4. Access the web interface via the generated public link: `Running on public URL: https://xxxx.gradio.live`.

### Model Installation (Google Drive)
Download your preferred SDXL `.safetensors` models (e.g., from Civitai or Hugging Face) and upload them to:
`My Drive/Fooocus/models/checkpoints/`

---

## 2. Local PC Setup

### Requirements
* Windows 10/11
* Python 3.10+
* NVIDIA or AMD GPU (4-6 GB VRAM minimum)

### Installation Steps
1. Clone the repository:
   ```bash
   git clone [https://github.com/lllyasviel/Fooocus.git](https://github.com/lllyasviel/Fooocus.git)
   cd Fooocus
