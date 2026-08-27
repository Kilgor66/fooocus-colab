# Fooocus Custom Colab & Local Setup Framework

An optimized deployment framework and launcher script for **Fooocus** (SDXL-based image generation engine). Designed for Google Colab with Google Drive storage persistence, custom checkpoint presets, and automated source fixes.
An optimized deployment framework and launcher script for Fooocus (SDXL-based image generation engine). Designed for Google Colab with Google Drive storage persistence, custom checkpoint presets, and automated source fixes. 100% free to run using Google Colab's free GPU tier — no paid API keys or subscriptions required.

---

## Key Features & Modifications

100% Free Cloud Execution: Runs on Google Colab's free GPU tier (T4) without requiring paid API credits, monthly subscriptions, or local high-end hardware.
* **Google Drive Persistence:** Downloaded `.safetensors` models, LoRAs, and generated images persist in Google Drive across Colab session resets.
* **`no_init_weights` Fix:** Automates an inline hotfix in `modules/patch_clip.py` to prevent execution crashes with recent PyTorch/Transformers releases.
* **Automated Model Download:** Automatically fetches the custom TalmendoXL checkpoint directly to your Google Drive on the first run.
* **Preset Override:** Configures `talmendoxlSDXL_v11Beta.safetensors` as the default base model inside `presets/default.json`.
* **High-VRAM Optimization:** Uses `--always-high-vram` and `--share` flags for optimal generation speeds and direct Gradio URL tunneling.

---

## Included Custom Model: TalmendoXL (Beta v1.1)

The Colab script is configured to automatically download the **TalmendoXL - Uncensored SDXL** base model if it is not already present on your system.

* **File Size:** ~6.6 GB
* **Download Location:** `My Drive/Fooocus/models/checkpoints/talmendoxlSDXL_v11Beta.safetensors`
* **Purpose & Style:** This model is designed to uncensor the base SDXL and bias the output towards high photorealism and non-professional photography. It creates images that look like amateur photos with highly natural lighting, intentionally avoiding overly polished, "studio-perfect" aesthetics. 
* **Creator Tips:** For the best results, use prompt keywords such as *"natural light"* and *"full body shot"*. Directional prompts like *"from the side"*, *"from the front"*, or *"from below"* are also highly effective.

---

## 1. Google Colab Setup (Cloud)

1. Open `fooocus_colab.ipynb` directly in Google Colab.
2. Run the code cell.
3. Authorize Google Drive access when prompted on the first run.
4. Access the web interface via the generated public link: `Running on public URL: https://xxxx.gradio.live`.

### Manual Model Installation (Google Drive)
If you want to add more SDXL `.safetensors` models (e.g., from Civitai or Hugging Face), upload them to:
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

    Apply patches (via Git Bash or WSL):
    Bash

    sed -i 's/with modeling_utils.no_init_weights():/if True:/g' modules/patch_clip.py
    sed -i 's/juggernautXL_v8Rundiffusion.safetensors/talmendoxlSDXL_v11Beta.safetensors/g' presets/default.json

    Run run.bat on Windows to launch.

Manual Model Installation (Local PC)

Place downloaded .safetensors model files inside the directory:
Fooocus/models/checkpoints/
Directory Structure
Plaintext

Fooocus/
├── models/
│   ├── checkpoints/      <-- Place SDXL base models here (.safetensors)
│   ├── loras/            <-- Place LoRA weights here
│   └── vae/              <-- VAE files
├── outputs/              <-- Generated images destination
├── presets/
│   └── default.json      <-- Default model settings
└── modules/
    └── patch_clip.py     <-- Patched CLIP module
