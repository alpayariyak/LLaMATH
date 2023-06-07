# Improving Mathematical Capabilities of Large Language Models

This repository will soon contain code for the finished project of fine-tuning LLaMA to improve its Mathematical capabiities.

# Installation

You can download and import this model into your project using the ```transformers``` library from Hugging Face:

1. Import the necessary modules
```
import torch
from transformers import LlamaForCausalLM, LlamaTokenizer, GenerationConfig
from peft import PeftModel
```

2. Load the base LLaMA 7B model and tokenizer
```
tokenizer = LlamaTokenizer.from_pretrained("yahma/llama-7b-hf")
model = LlamaForCausalLM.from_pretrained(
    'yahma/llama-7b-hf',
    load_in_8bit=True,
    torch_dtype=torch.float16,
    device_map="auto")
```

3. Apply the MATHLLaMA delta weights
```
model = PeftModel.from_pretrained(model, 'alpayariyak/MATHLLaMA', torch_dtype=torch.float16, force_download=True)
```
