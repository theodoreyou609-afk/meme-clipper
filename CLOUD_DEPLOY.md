# Cloud Deployment Guide: ComfyUI on RunPod (No Local GPU)

This guide lets you run a full ComfyUI backend accessible from your iPhone Safari, and connect it to the custom frontend in this repo.

## Why RunPod?

- Official ComfyUI templates
- Easy public proxy URLs (HTTPS)
- Network Volumes so models persist between sessions
- Pay only while the pod is running

## Step-by-Step

1. Sign up at https://runpod.io (add payment method for GPU). **This requires your account.**
2. Navigate to **Pods** → **Deploy**.
3. Search for "ComfyUI" templates (official or community). Prefer ones with recent ComfyUI + CUDA.
4. Select GPU:
   - RTX 3090 / 4090 (24 GB) for SDXL + IP-Adapter.
   - Higher if using Flux.
5. (Optional but recommended) Create and attach a **Network Volume** (e.g., 50–100 GB) mounted at `/workspace` so models and outputs persist. **Requires your account.**
6. Deploy the pod. **This incurs cost while running — stop when done.**
7. Once running, click the **Connect** or proxy link for port 8188. Example format:
   `https://xxxxxxxx-8188.proxy.runpod.net`
8. Open that URL in iPhone Safari to confirm ComfyUI loads.
9. In ComfyUI (on the pod):
   - Use Manager to install custom nodes if needed (IP-Adapter for character consistency, etc.).
   - Download models (e.g. SDXL) into the models folder (use the volume).
   - Test a basic workflow.
10. **Enable CORS for the frontend** (important for browser access from GitHub Pages or local file):
    - In the pod terminal or launch args, ensure ComfyUI starts with `--enable-cors-header "*"` (many templates support custom launch arguments; check template docs or edit start script).
    - Restart the pod if needed.
11. For the custom frontend in this repo:
    - **GitHub Pages**: Settings → Pages → Deploy from branch `main` / root. The page will be available at `https://theodoreyou609-afk.github.io/meme-clipper/`.
    - Or open `index.html` directly in Safari.
    - Set the API URL field to your RunPod proxy address (e.g. `https://xxxxxxxx-8188.proxy.runpod.net`).
    - Use the **Test Connection / CORS** button to verify.
    - Use **List Available Models** to see checkpoints on the pod and pick one.
    - Set the model name to match exactly.
    - Upload image, enter prompt, generate.

## Frontend Features Implemented

- Configurable ComfyUI endpoint (saved in localStorage).
- Connection test and model listing (requires CORS).
- Image upload via `/upload/image` (safe filename).
- Prompt submission with basic img2img workflow (LoadImage → VAEEncode → KSampler → VAEDecode → SaveImage).
- Checkpoint name validation (non-empty + common extensions).
- Generation status polling via `/history` with improved error detection (status, messages, node_errors on queue).
- Result preview via `/view` and download (blob-based for better Safari support).
- Error handling, loading indicators, and status messages.
- Works in mobile Safari (file input, fetch, FormData).

**Note**: The built-in workflow is a simple img2img. For advanced character consistency, IP-Adapter, inpainting, etc., export your own API-format workflow from ComfyUI and extend the frontend `buildWorkflow` function, or load custom JSON.

**Audit status** (code review only; no live RunPod runtime test performed):
- Workflow graph, LoadImage reference, and KSampler/VAE connections are valid ComfyUI API format.
- CORS must be enabled on the pod for the frontend to work from GitHub Pages or file://.
- Download uses blob + object URL when CORS allows; falls back to direct link.

## Cost Control

- Stop the pod when finished (you only pay for runtime).
- Use Community Cloud for lower prices.
- Monitor usage in the RunPod dashboard.
- Network volume storage is billed separately.

## Alternatives

- **Vast.ai**: Often cheaper; search for ComfyUI Docker templates.
- **Comfy Cloud**: Official, zero setup, higher cost, fewer custom nodes initially.

## Security Note

RunPod proxy URLs are public if shared. Use strong passwords if the template supports auth, or stop the pod when not in use. Do not share the proxy URL publicly.

No models are pre-installed by this repository. You download them yourself on the cloud instance.

## Manual Steps Requiring Your Account Access

- Creating RunPod account and adding payment method.
- Deploying the pod and attaching Network Volume.
- Downloading models on the pod.
- Enabling CORS / configuring launch arguments if not default.
- Stopping the pod to avoid charges.
- Enabling GitHub Pages (optional) if you want a public URL for the frontend.
