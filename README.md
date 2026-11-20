# AI Image Editor for Fictional Adult Characters

Mobile-optimized browser interface for image-to-image editing, inpainting, clothing/fashion transformations (bikini, lingerie, glamour, boudoir styles), pose adjustments, and character identity preservation.

**Important**: This is a frontend only. Backend requires a cloud GPU service running ComfyUI. No models have been installed, executed, or tested in this repository. No local GPU is required. Works on iPhone Safari.

## Cloud Deployment (No Local GPU Needed)

Since you only have an iPhone, use a cloud GPU provider. Recommended primary option: **RunPod**.

See [CLOUD_DEPLOY.md](CLOUD_DEPLOY.md) for full step-by-step instructions, including how to connect this frontend to your ComfyUI pod.

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

1. Create a free account at https://www.runpod.io (**your account**)
2. Go to Pods → Deploy
3. Select a ComfyUI template
4. Choose GPU (RTX 4090 or 3090 for SDXL)
5. Add a Network Volume for persistent models if desired
6. Deploy. Wait for it to start. **Incurs cost while running.**
7. Access the ComfyUI UI via the provided proxy URL (e.g., `https://<pod-id>-8188.proxy.runpod.net`)
8. From your iPhone Safari, open that URL. Install models, enable CORS if needed (`--enable-cors-header "*"`).
9. Open this repo's `index.html` (or enable GitHub Pages on `main` / root) and set the API URL field to the same proxy address. Use the Test Connection and List Models buttons.
10. Upload image, enter prompt, generate.

**Character identity consistency**: In ComfyUI, load IP-Adapter (or similar) custom nodes and a reference image of your fictional character. Extend the frontend workflow for advanced features.

**Image-to-image & inpainting**: Basic img2img is implemented. For masked inpainting, customize the workflow.

### Implemented vs. Requires External Service

| Feature | Status | Notes |
|---------|--------|-------|
| Mobile frontend (upload, prompts, preview, download) | **Fully implemented** | Open `index.html`; communicates with ComfyUI API |
| Configurable ComfyUI endpoint | Implemented | Saved in browser localStorage |
| Generation status + error handling + loading | Implemented | Polls /history, improved error detection |
| Connection / model list tests | Implemented | Requires CORS |
| Checkpoint validation | Implemented | Non-empty + common extensions |
| Safari-friendly download | Implemented | Blob + object URL when CORS allows |
| Cloud GPU hosting | Requires external paid service (RunPod etc.) | Not free; stop pod when done |
| ComfyUI + models | Requires you to deploy on cloud | Templates help; you download models |
| Character consistency (IP-Adapter etc.) | Supported by ComfyUI workflows | Configure in the cloud instance; extend frontend if needed |
| Image-to-image / inpainting | Basic img2img implemented | Use appropriate workflow for advanced |
| Public web interface | Yes via cloud proxy + frontend | Accessible from iPhone Safari; GitHub Pages ready |

**No local installation required.**

## Selected Backend: ComfyUI

- Most powerful for character consistency, inpainting, fashion edits.
- Cloud templates make it accessible without a PC.
- Frontend uses standard ComfyUI API endpoints: `/upload/image`, `/prompt`, `/history/{id}`, `/view`, `/system_stats`, `/models/checkpoints`.

**Audit note**: Workflow structure, LoadImage reference, and KSampler/VAE connections verified as valid API format via code review. No live runtime test against a RunPod instance was performed.

**Use only fictional adult characters. Do not generate non-consensual imagery of real people.**

## Disclaimer

This repository contains only the frontend and documentation. Actual generation requires a paid cloud GPU service and your own model downloads. You are responsible for costs, licensing, and legal use. Do not incur GPU expenses without authorization.

## Manual Steps Requiring Your Account

- RunPod account creation, payment method, pod deployment, model downloads, CORS configuration, and stopping the pod.
- Optional: enable GitHub Pages for a public frontend URL.
