# Open LLM

- [Open LLM on HuggingFace](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard)
- [Open LLM on Github](https://github.com/bentoml/OpenLLM)



## YT references 
- [Mathew API for Open-Source](https://www.youtube.com/watch?v=8nZZ2oQhx4E&ab_channel=MatthewBerman)
- [Abhishek Open AI LLM](https://www.youtube.com/watch?v=o1BCq1KJULM&t=1022s&ab_channel=AbhishekThakur)


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
