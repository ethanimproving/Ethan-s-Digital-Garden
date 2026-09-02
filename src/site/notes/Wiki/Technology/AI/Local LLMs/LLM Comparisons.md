---
{"dg-publish":true,"permalink":"/wiki/technology/ai/local-ll-ms/llm-comparisons/","dg-note-properties":{}}
---


According to Artificial Analysis, the most intelligent LLMs per dollar are:

| Model                  | Intelligence | $ / Task | $ / M TOK                                                    | SWE bench Verified                                                                  |
| ---------------------- | ------------ | -------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| Grok 4.5               | 54           | .31      | [$2](https://openrouter.ai/x-ai/grok-4.5)                    | [86.6%](https://genztech.blog/models/grok-4-5/?utm_source=perplexity)               |
| GPT 5.6 Luna (MAX)     | 51           | .21      | [$0.50](https://openrouter.ai/openai/gpt-5.6-luna-pro)       |                                                                                     |
| Muse Spark 1.1         | 51           | .26      | [$1.25](https://openrouter.ai/meta/muse-spark-1.1#providers) |                                                                                     |
| ==GLM 5.2==            | 51           | .32      | [$0.67](https://openrouter.ai/z-ai/glm-5.2)                  | [78.7%](https://thevibefather.com/blog/glm-5-2-coding-review?utm_source=perplexity) |
| MiniMax M3             | 44           | .12      | [$0.24](https://openrouter.ai/minimax/minimax-m3)            | [80.5%](https://huggingface.co/datasets/SWE-bench/SWE-bench_Verified)               |
| DeepSeek V4 Pro (high) | 43           | .04      | [$0.44](https://openrouter.ai/deepseek/deepseek-v4-pro)      | [80.6%](https://huggingface.co/datasets/SWE-bench/SWE-bench_Verified)               |
| Kimi K3                | 57           | .95      | [$3](https://openrouter.ai/moonshotai/kimi-k3)               | [93.4%](https://genztech.blog/models/kimi-k3/?utm_source=perplexity)                |


![](https://i.imgur.com/jA8jMr1.jpeg)
 [^1]

# Cheapest Models


| Model             | $ / M TOK                                                         | SWE bench Verified                                                                                                     |                                                                              |
| ----------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| DeepSeek V4 Flash | [$0.09](https://openrouter.ai/deepseek/deepseek-v4-flash)         | [73.7%](https://benchlm.ai/benchmarks/sweVerified?utm_source=perplexity)                                               | [42](https://artificialanalysis.ai/models/deepseek-v4-flash-0420)            |
| DeepSeek V4 Flash | [$0.03](https://openrouter.ai/deepseek/deepseek-v4-flash-0731)    | [73.7%](https://benchlm.ai/benchmarks/sweVerified?utm_source=perplexity)                                               | [52](https://artificialanalysis.ai/models/deepseek-v4-flash)                 |
| Nemotron 3 Super  | [$0.085](https://openrouter.ai/nvidia/nemotron-3-super-120b-a12b) | [55%](https://www.digitalapplied.com/blog/nemotron-3-super-120b-nvidia-open-source-coding-model?utm_source=perplexity) | [26](https://artificialanalysis.ai/models/nvidia-nemotron-3-super-120b-a12b) |
| Qwen3.6 35B A3B   | [$0.10](https://openrouter.ai/qwen/qwen3.6-35b-a3b)               | [73.4%](https://qwen.ai/blog?id=qwen3.6-35b-a3b&utm_source=perplexity)                                                 | [32](https://artificialanalysis.ai/models/qwen3-6-35b-a3b)                   |
| GPT-5 Nano        | [$0.05](https://openrouter.ai/openai/gpt-5-nano)                  | [34.8%](https://sambanova.ai/blog/are-llms-truly-solving-software-problems?utm_source=perplexity)                      | [20](https://artificialanalysis.ai/models/gpt-5-nano)                        |
| Ling 3.0          | [$0.02](https://openrouter.ai/inclusionai/ling-3.0-flash)         | [56.6%](https://huggingface.co/inclusionAI/Ling-3.0-flash) (Pro)                                                       | [38](https://artificialanalysis.ai/models/ling-3-0-flash)                    |
| GLM-5.3 Flash     | [$0.08](https://openrouter.ai/z-ai/glm-5.3-flash)                 |                                                                                                                        | [57](https://artificialanalysis.ai/models/glm-5-3-flash)                     |


# Local models

| Model                |                                                               | SWE bench Pro                                               |
| -------------------- | ------------------------------------------------------------- | ----------------------------------------------------------- |
| Qwen3.8-27B (xhigh)  | [52](https://artificialanalysis.ai/models/qwen3-8-27b)        | [61.7](https://huggingface.co/Qwen/Qwen3.8-27B)             |
| Qwen3.8-27B (medium) | [44](https://artificialanalysis.ai/models/qwen3-8-27b-medium) | -                                                           |
| Qwen3.6-27B          | [38](https://artificialanalysis.ai/models/qwen3-6-27b)        | [53.5](https://huggingface.co/Qwen/Qwen3.8-27B)             |
| Qwen3.6 35B A3B      | [32](https://artificialanalysis.ai/models/qwen3-6-35b-a3b)    | [49.5](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) |
| Ornith-1.5-35B-A3B   |                                                               | [59.6](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) |
| Muse Glimmer         |                                                               | [51.2](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) |


---
[^1]: “[Intelligence Index vs. Cost per Intelligence Index Task](https://artificialanalysis.ai/models#intelligence-comparison-tabs).” *Artificial Analysis*. July 2026. 