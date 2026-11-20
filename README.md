# AI Image Editor for Fictional Adult Characters

Mobile-optimized browser interface for image-to-image editing, inpainting, clothing/fashion transformations (bikini, lingerie, glamour, boudoir styles), pose adjustments, and character identity preservation.

**Important**: This is a frontend only. Backend requires a cloud GPU service running ComfyUI. No models have been installed, executed, or tested in this repository. No local GPU is required.

## Cloud Deployment (No Local GPU Needed)

Since you only have an iPhone, use a cloud GPU provider. Recommended primary option: **RunPod**.

### Cloud Options Comparison (approx. Nov 2026 prices)

| Provider | Ease of Use | Typical Cost (RTX 4090 / 24GB) | Public Access | Notes | Best For |
|----------|-------------|-------------------------------|---------------|-------|----------|
| **RunPod** | High (official ComfyUI templates) | ~$0.34–$0.89/hr (Community/Secure) | Yes (proxy URL) | Official templates, Network Volumes for models, serverless option | **Recommended** |
| **Vast.ai** | Medium (marketplace) | Often cheaper (~$0.20–$0.60/hr) | Yes | Lowest cost but more variable reliability | Budget users |
| **Comfy Cloud** (official) | Highest | Subscription or higher hourly | Yes | Zero setup, limited custom nodes | Absolute beginners |
| Hugging Face Spaces | Medium | Free tier limited; paid GPU | Yes | Good for demos | Sharing |
| Others (Lambda, Paperspace) | Medium | Varies | Yes | Solid alternatives | - |

**Cost estimate example**: 2-hour session on RTX 4090 ≈ $1–$2 on RunPod. Storage (network volume) extra (~$0.07/GB/month). Stop the pod when not in use.

### Quick Start with RunPod (Recommended)

1. Create a free account at https://www.runpod.io
2. Go to Pods → Deploy
3. Select a ComfyUI template (official ones available, e.g., with CUDA support)
4. Choose GPU (RTX 4090 or 3090 for SDXL; higher for Flux)
5. Add a Network Volume for persistent models if desired
6. Deploy. Wait for it to start.
7. Access the ComfyUI UI via the provided proxy URL (e.g., `https://<pod-id>-8188.proxy.runpod.net`)
8. From your iPhone Safari, open that URL. Upload images, run workflows.
9. Point this frontend's API URL field to the same proxy address if using the custom frontend.

**Character identity consistency**: In ComfyUI, load IP-Adapter (or similar) custom nodes and a reference image of your fictional character.

**Image-to-image & inpainting**: Use standard ComfyUI img2img or masked inpainting workflows.

### Implemented vs. Requires External Service

| Feature | Status | Notes |
|---------|--------|-------|
| Mobile frontend (upload, prompts, preview, download) | Implemented in this repo | Open `index.html` or host it |
| Cloud GPU hosting | Requires external paid service (RunPod etc.) | Not free |
| ComfyUI + models | Requires you to deploy on cloud | Templates help; you download models |
| Character consistency (IP-Adapter etc.) | Supported by ComfyUI workflows | Configure in the cloud instance |
| Image-to-image / inpainting | Supported by ComfyUI | Use appropriate workflow |
| Public web interface | Yes via cloud proxy | Accessible from iPhone |

**No local installation required.**

## Selected Backend: ComfyUI

- Most powerful for character consistency, inpainting, fashion edits.
- Cloud templates make it accessible without a PC.

**Use only fictional adult characters. Do not generate non-consensual imagery of real people.**

## Disclaimer

This repository contains only the frontend and documentation. Actual generation requires a paid cloud GPU service and your own model downloads. You are responsible for costs, licensing, and legal use.
