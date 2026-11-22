# OverHeard reader voices

Browser-ready reader voices for [OverHeard](https://github.com/BPMData/OverHeard), served from
GitHub Pages (CORS `*`) at `https://bpmdata.github.io/overheard-voices/`.

## Meta MMS text-to-speech (`mms-tts-<iso3>/`)

| Folder | Language | Source model |
| --- | --- | --- |
| `mms-tts-swh` | Swahili | [facebook/mms-tts-swh](https://huggingface.co/facebook/mms-tts-swh) |
| `mms-tts-hat` | Haitian Creole | [facebook/mms-tts-hat](https://huggingface.co/facebook/mms-tts-hat) |
| `mms-tts-som` | Somali | [facebook/mms-tts-som](https://huggingface.co/facebook/mms-tts-som) |
| `mms-tts-ind` | Indonesian | [facebook/mms-tts-ind](https://huggingface.co/facebook/mms-tts-ind) |
| `mms-tts-tur` | Turkish | [facebook/mms-tts-tur](https://huggingface.co/facebook/mms-tts-tur) |

Each folder holds `model_quantized.onnx` (the VITS model exported to ONNX, opset 17, with
Hugging Face Optimum 1.27.0, Transformers 4.46.3 and PyTorch 2.5.1, with its weights stored as
8-bit integers that the graph turns back into float; about 28 MB) and the original `vocab.json`.
How they were made: `docs/mms-voices.md` in the OverHeard repository.

`mms-tts-ind/model_quantized_rate088.onnx` is Indonesian exported with `speaking_rate` 0.88
(about 10% slower than Meta's default, which sounded rushed); OverHeard uses that one.

**Attribution and license.** These models are from Meta AI's Massively Multilingual Speech
project: Pratap et al., *Scaling Speech Technology to 1,000+ Languages* (2023),
[arXiv:2305.13516](https://arxiv.org/abs/2305.13516). They are licensed under
[Creative Commons Attribution-NonCommercial 4.0](https://creativecommons.org/licenses/by-nc/4.0/)
(CC BY-NC 4.0). The only change made here is the format conversion and weight quantization described
above. Non-commercial use only.
