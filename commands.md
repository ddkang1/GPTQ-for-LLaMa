```shell
pip install -e .

CUDA_VISIBLE_DEVICES=0 python llama.py ~/models/vicuna-13b-v1.1 c4 --wbits 4 --true-sequential --act-order --groupsize 128 --save vicuna-13b-4bit-128g.v1.1.pt
CUDA_VISIBLE_DEVICES=0 python -m gptq_for_llama.llama_inference ~/models/vicuna-13b-v1.1 --wbits 4 --groupsize 128 --load ~/models/vicuna-13b-4bit-128g.v1.1.pt --text "this is llama"

CUDA_VISIBLE_DEVICES=0 python starcoder.py bigcode/starcoder stack --wbits 4 --true-sequential --act-order --groupsize 128 --save starcoder-GPTQ-4bit-128g.pt
CUDA_VISIBLE_DEVICES=0 python starcoder.py bigcode/starcoder stack --wbits 4 --true-sequential --act-order --groupsize 128 --save_safetensors starcoder-GPTQ-4bit-128g.safetensors
CUDA_VISIBLE_DEVICES=0 python -m gptq_for_llama.starcoder_inference ~/models/starcoder --wbits 4 --groupsize 128 --load ~/models/starcoder-GPTQ-4bit-128g.pt

```