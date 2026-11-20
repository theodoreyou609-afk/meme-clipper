# AI Image Editor for Fictional Adult Characters

Mobile-optimized browser interface for image-to-image editing, inpainting, clothing/fashion transformations (bikini, lingerie, glamour, boudoir styles), pose adjustments, and character identity preservation.

**Important**: This is a frontend only. It requires a separately installed and running ComfyUI instance with appropriate models. No models have been installed, executed, or tested in this repository.

## Selected Backend: ComfyUI

After evaluating open-source options:

- **ComfyUI** (recommended): Most powerful, modular, actively developed. Supports advanced workflows for character consistency (IP-Adapter, InstantID, PuLID, etc.), inpainting, ControlNet for poses, custom nodes. Best for fashion/glamour edits while preserving identity. Hardware: NVIDIA GPU with 8GB+ VRAM recommended (SDXL), 12GB+ preferred for Flux or heavy workflows.
- **AUTOMATIC1111 WebUI**: Classic interface, good extensions for inpainting. Less flexible for complex character workflows. Updates slowed.
- **Fooocus**: Simplest for beginners, SDXL focused, has inpainting. Limited long-term support and less control.
- Others (e.g., OpenGPEX): Browser-native with optional ComfyUI bridge.

ComfyUI is the most suitable for the required features.

### Licensing & Hardware

- Software: ComfyUI is open source (GPL-3.0).
- Models: SD 1.5 / SDXL under OpenRAIL licenses (with conditions). Flux.1 dev is non-commercial; Flux.1 schnell is Apache 2.0. User must check specific checkpoint/LoRA licenses.
- Hardware: Minimum ~8GB VRAM for SDXL. 12-16GB recommended. CPU-only is impractical. System RAM 16GB+ , storage for models (several GB each).

### Features Supported (via proper ComfyUI workflows)

- Image-to-image transformation
- Inpainting and masking
- Character identity preservation (IP-Adapter, etc.)
- Fashion, bikini, lingerie, glamour, boudoir styles (via prompts + models)
- Pose/body adjustments (ControlNet OpenPose, etc.)
- Realistic skin/lighting (quality models + prompts)
- High-res exports

**Use only fictional adult characters. Do not generate non-consensual imagery of real people.**

## Setup

1. Install ComfyUI separately on a machine with a suitable GPU: https://github.com/Comfy-Org/ComfyUI
2. Install required custom nodes (e.g., IPAdapter, ControlNet, Inpaint nodes).
3. Download models (checkpoints, IP-Adapters, etc.) into ComfyUI folders.
4. Run ComfyUI with `--listen` for network access if using from another device (phone).
5. Serve this frontend (or open index.html) and set the ComfyUI API URL (e.g., http://your-pc-ip:8188).
6. Configure/load a suitable workflow for img2img + inpainting + character reference.

This frontend is a starting point. Advanced features require custom ComfyUI workflows matching your models.

## Mobile Optimization

Designed for iPhone Safari: responsive, touch-friendly, large buttons, file upload, canvas preview.

## Disclaimer

No models or backend have been installed or tested here. You are responsible for hardware, model downloads, licensing compliance, and legal use of generated content.
