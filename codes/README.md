# AutoAd: Automated Video Ad Generation on Kaggle

A fully automated pipeline for generating short advertisement videos from a single product image, powered by open-weight models running on Kaggle's free GPU tier.

## Prerequisites

- A [Kaggle](https://www.kaggle.com/) account with GPU access enabled
- A [Groq](https://console.groq.com/) API key (free tier)

## Setup

### Step 1: Download Model Weights

Run each of the following notebooks **separately** on Kaggle. After each notebook finishes, **save the output as a Kaggle Dataset** so the weights can be reused without re-downloading.

| Notebook | Description | Save As Dataset |
|---|---|---|
| `qwen-download.ipynb` | Downloads Qwen text-to-image model weights | `qwen-weights` |
| `sam3-download.ipynb` | Downloads SAM 3 segmentation model weights | `sam3-weights` |
| `wan2-2-download.ipynb` | Downloads Wan 2.2 image-to-video model weights | `wan2-2-weights` |

Extra: Download `edit_0928_lora_step40000.safetensors` [here](https://huggingface.co/DiffSynth-Studio/Qwen-Image-Edit-F2P/blob/c06e0c518e05bd5a8e08b707ee1c9b7954918b76/edit_0928_lora_step40000.safetensors) and save it as a Kaggle Dataset named `lora_models`.

> **How to save as a dataset:**  
> After a notebook run completes, go to the **Output** tab → click **New Dataset** → give it a name → **Save**.

### Step 2: Set Up Groq API Key

1. Go to [console.groq.com](https://console.groq.com/) and create a free account.
2. Generate an API key from the dashboard.
3. In your Kaggle notebook, add the key as a **Kaggle Secret**:
   - Go to **Add-ons** → **Secrets** → add a new secret named `GROQ_API_KEY` with your key as the value.

### Step 3: Run the Pipeline

1. Open `ads_generation_framework_kaggle.ipynb` on Kaggle.
2. Under **Data Sources**, attach the three datasets you saved in Step 1.
3. Make sure the Groq API secret is enabled for this notebook.
4. Run all cells.

## Colab Setup (Google Drive)

### Step 1: Download Model Weights to Drive

1. Open `datasets_download_colab.ipynb` in Colab.
2. Set the runtime to **GPU** (Runtime -> Change runtime type -> GPU).
3. Run all cells to mount Drive and download the weights to:
   - `/content/drive/MyDrive/646final/models_download`

> If you want a different Drive folder, update `save_path` in
> `datasets_download_colab.ipynb` and also update `MODEL_SOURCE_PATH` in
> `ads_generation_framework_colab.ipynb` to match.

### Step 2: Set Up Groq API Key (Colab)

1. Go to [console.groq.com](https://console.groq.com/) and create a free account.
2. Generate an API key from the dashboard.
3. In Colab, open the **Secrets** panel (key icon) and add a secret named
   `GROQ_API_KEY` with your key as the value.

### Step 3: Run the Colab Pipeline

1. Open `ads_generation_framework_colab.ipynb` in Colab.
2. Confirm it points to the same Drive folder used in Step 1.
3. Run the *first* cells.


