
# Exploring Options to deploy LLM

1. Open LLM
2. text-generation-inference
3. LocalGPT

<hr />

# 1. Open LLM

## YT references 
- [Mathew API for Open-Source](https://www.youtube.com/watch?v=8nZZ2oQhx4E&ab_channel=MatthewBerman)

## Links 
- [Open LLM on HuggingFace](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard)
- [Open LLM on Github](https://github.com/bentoml/OpenLLM)


## Features
- 🚂 State-of-the-art LLMs: built-in supports a wide range of open-source LLMs and model runtime, including Llama 2，StableLM, Falcon, Dolly, Flan-T5, ChatGLM, StarCoder and more.
- 🔥 Flexible APIs: serve LLMs over RESTful API or gRPC with one command, query via WebUI, CLI, our Python/Javascript client, or any HTTP client.
- ⛓️ Freedom To Build: First-class support for LangChain, BentoML and Hugging Face that allows you to easily create your own AI apps by composing LLMs with other models and services.
- 🎯 Streamline Deployment: Automatically generate your LLM server Docker Images or deploy as serverless endpoint via ☁️ [BentoCloud](https://www.bentoml.com/cloud)
- 🤖️ Bring your own LLM: Fine-tune any LLM to suit your needs with LLM.tuning(). (Coming soon)

## How to use?
- Windows native verv or WSL
    - Cretae a new conda environment (it will support python ? 3.8)<br>
    (base)>> conda create -n open-llm python==3.11.3<br>
    (base)>> conda activate open-llm <br> <br>

    - install the default LLM or Install llama-2 use:<br>
    (open-llm) >> pip install openllm <br>
    or <br>
    (open-llm) >> pip install "openllm[llama]" <br> <br>
    
    - get help <br>
    (open-llm) >> openllm -h <br>
    (open-llm) >> openllm start opt <br> 
    or <br>
    (open-llm) >> openllm start llama <br> 
    server is up and running <br> 
    or <br>
    openllm start flan-t5 --model-id google/flan-t5-large <br>

- Python code to call the API <br>
    import openllm <br>
    llm = openllm.client.HTTPClient("http://localhost:3000") <br>
    response = llm.query("What is the difference between 'further' and 'farther'"?)<br>
    
- Deployment 
    - (open-llm) >> openllm build llama <br>
    This packs 'llama' into a Bento with kwargs={}...

<hr />

# 2. text-generation-inference

## YT references 
- [Abhishek Open AI LLM](https://www.youtube.com/watch?v=o1BCq1KJULM&t=1022s&ab_channel=AbhishekThakur)
- Recommended to use it with Docker. [Docker Tutorial](https://www.youtube.com/watch?v=8vmKtS8W7IQ&list=PLLcUibM4B4Q_2ezE6pqgYYLFGp6rPJ5Je&index=20&ab_channel=KrishNaik)



## Links 
- [text-generation-inference on HuggingFace](https://huggingface.co/text-generation-inference)
- [text-generation-inference on Github](https://github.com/huggingface/text-generation-inference)
- [tgi Dockerfile](https://github.com/huggingface/text-generation-inference/blob/main/Dockerfile)
- Integrate with [Chat-ui](https://github.com/huggingface/chat-ui)

## Features

## How to use?
- Open VS Code 
- Open Terminal
- Git Hub approiach 
    - model=tiiuae/falcon-7b-instruct volume=$PWD/data # share a volume with the Docker container to avoid downloading weights every run
    - (chat-ui) >> docker run --gpus all --shm-size 1g -p 8080:80 -v $volume:/data ghcr.io/huggingface/text-generation-inference:1.0.0 --model-id $model

OR 
- Abhishek's approach
    - (chat-ui) >> docker run --gpus all -p 3000:80 -v /data:/data -e LOG_LEVEL = infor, text_generation_router = debug ghcr.io/huggingface/text-generation-inference:1.0.0 --model-id meta-llama/Llama-2-13b-chat-hf --num-shard 1

    - quantize edit:
    meta-llama/Llama-2-13b-chat-hf, quantize: 

- Open browser 
127.0.0.1:3000/docs

- chat ui runs on port 5173


- Use it in python 
    - pip install text-generation
    - Python Code:
from text_generation import Client

client = Client("http://127.0.0.1:3000")
print(client.generate("What is Deep Learning?", max_new_tokens=20).generated_text)

text = ""
for response in client.generate_stream("What is Deep Learning?", max_new_tokens=20):
    if not response.token.special:
        text += response.token.text
print(text)

<hr />

# 3. LocalGPT

## YT references 
- [Local GPT](https://www.youtube.com/watch?v=lbFmceo4D5E&t=934s&ab_channel=PromptEngineering)

## Links 
- [LocalGPT on Github](https://github.com/PromtEngineer/localGPT)
