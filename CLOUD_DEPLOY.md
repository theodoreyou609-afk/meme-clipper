# Cloud Deployment Guide: ComfyUI on RunPod (No Local GPU)

This guide lets you run a full ComfyUI backend accessible from your iPhone Safari.

## Why RunPod?

- Official ComfyUI templates
- Easy public proxy URLs
- Network Volumes so models persist between sessions
- Pay only while the pod is running

## Step-by-Step

1. Sign up at https://runpod.io (add payment method for GPU).
2. Navigate to **Pods** → **Deploy**.
3. Search for "ComfyUI" templates (official or community).
4. Select GPU:
   - RTX 3090 / 4090 (24 GB) for SDXL + IP-Adapter.
   - Higher if using Flux.
5. (Optional but recommended) Create and attach a **Network Volume** (e.g., 50–100 GB) mounted at `/workspace` so models and outputs persist.
6. Deploy the pod.
7. Once running, click the **Connect** or proxy link for port 8188. Example format:
   `https://xxxxxxxx-8188.proxy.runpod.net`
8. Open that URL in iPhone Safari.
9. In ComfyUI:
   - Install custom nodes via Manager (IP-Adapter, ControlNet, etc.).
   - Download models into the volume.
   - Load or build a workflow for img2img + character reference.
10. For the custom frontend in this repo: host `index.html` (GitHub Pages, or open locally) and set the API URL to your RunPod proxy address.

## Cost Control

- Stop the pod when finished (you only pay for runtime).
- Use Community Cloud for lower prices.
- Monitor usage in the RunPod dashboard.

## Alternatives

- **Vast.ai**: Often cheaper; search for ComfyUI Docker templates.
- **Comfy Cloud**: Official, zero setup, higher cost, fewer custom nodes initially.

## Security Note

RunPod proxy URLs are public if shared. Use strong passwords if the template supports auth, or stop the pod when not in use.

No models are pre-installed by this repository. You download them yourself on the cloud instance.
