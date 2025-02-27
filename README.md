# texifast ![Python Version from PEP 621 TOML](https://img.shields.io/python/required-version-toml?tomlFilePath=https%3A%2F%2Fraw.githubusercontent.com%2FSped0n%2Ftexifast%2Fmain%2Fpyproject.toml) ![PyPI - Version](https://img.shields.io/pypi/v/texifast) ![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/Sped0n/texifast/pytest.yml?label=pytest)

LaTeX and markdown OCR powered by [texify](https://github.com/VikParuchuri/texify), without bloated dependencies like torch or transformers.

## Features

- Minimal dependency graph
- Compared to [Optimum](https://github.com/huggingface/optimum), texifast is faster (~20%) and has a smaller memory footprint (~20%). For details, see [benchmark](https://github.com/Sped0n/texifast/tree/main/benchmark).
- Supports IOBinding features of ONNXRuntime and optimizes for CUDAExecutionProvider.
- Supports quantized/mixed precision models.

## Installation

You must implicitly specify the required dependencies.

```
pip install texifast[cpu]
# or if you want to use CUDAExecutionProvider
pip install texifast[gpu]
```

> ⚠️⚠️⚠️
>
> **Do not install with** `pip install texifast` **!!!**

## Quickstart

This quick start use the [image in test folder](https://raw.githubusercontent.com/Sped0n/texifast/main/tests/latex.png), you can use whatever you like.

```python
from texifast.model import TxfModel
from texifast.pipeline import TxfPipeline

model = TxfModel(
    encoder_model_path="./encoder_model_quantized.onnx",
    decoder_model_path="./decoder_model_merged_quantized.onnx",
)
texifast = TxfPipeline(model=model, tokenizer="./tokenizer.json")
print(texifast("./latex.png"))
```

> You can download the quantized ONNX model [here](https://huggingface.co/Spedon/texify-quantized-onnx/tree/main) and the FP16 ONNX model [here](https://huggingface.co/Spedon/texify-fp16-onnx/tree/main).

## API

The full Python API documentation can be found [here](https://github.com/Sped0n/texifast/tree/main/docs).

## Credits

- https://github.com/VikParuchuri/texify
- https://github.com/MosRat/MixTex-rs
- https://github.com/xenova/transformers.js
- https://onnxruntime.ai/docs/api/python/api_summary.html
- https://github.com/ml-tooling/lazydocs
