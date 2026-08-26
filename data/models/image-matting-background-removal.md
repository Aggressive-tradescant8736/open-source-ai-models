# Image Matting & Background Removal

Subcategory tree: General · Human/Portrait · Clothing · Animal · Product · Anime/Illustration.
Do not assume every segmentation model is a background-removal model — classify by actual intended use.

| Model | Size | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| [BiRefNet](https://github.com/ZhengPeng7/BiRefNet) | ~880 MB (weights) | Dichotomous Image Segmentation / Matting | CPU/GPU | MIT | High-resolution background removal, General |

## Notes

- **BiRefNet** ("Bilateral Reference Network") targets high-resolution dichotomous image segmentation and is widely used as the backbone for general-purpose background removal tools (e.g. via the `rembg` and `transformers.js` ecosystems).
- Officially released by ZhengPeng7 (CAAI AIR '24 paper) under MIT license — free for commercial use.
- Community wrapper projects (browser extensions, WebUI plugins) built on top of BiRefNet may carry their own separate licenses independent of the model weights; verify the wrapper's license separately if redistributing it.

This category currently has one verified entry. U2-Net, U2-Net Human/Cloth, and IS-Net variants are on the roadmap — contributions verifying their current license and specs are welcome. See [CONTRIBUTING.md](../../CONTRIBUTING.md).
