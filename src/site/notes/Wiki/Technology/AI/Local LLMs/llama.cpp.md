---
{"dg-publish":true,"permalink":"/wiki/technology/ai/local-ll-ms/llama-cpp/","created":"Apr 2, 2020, 9:23 PM","dg-note-properties":{}}
---

# Install

Visit the current release page for [llama.cpp](https://github.com/ggml-org/llama.cpp) on GitHub and download the `Windows x64 (CUDA 13)` package as well as the `cudart-llama-bin-win-cuda-13.3-x64.zip`. Extract the files under Program Files and add to System Path.

# Download Models

- [Qwen3.8-27B](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF?show_file_info=Qwen3.8-27B-UD-Q4_K_M.gguf)
- [Qwen3-Coder-30B-A3B](https://huggingface.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF?show_file_info=Qwen3-Coder-30B-A3B-Instruct-Q4_K_M.gguf)
- [Gemma-3-27B](https://huggingface.co/unsloth/gemma-3-27b-it-GGUF?show_file_info=gemma-3-27b-it-Q4_K_M.gguf)
- [GPT-OSS-20B](https://huggingface.co/Userb1az/gpt-oss-20b-GGUF?show_file_info=gpt-oss-20b-MXFP4_MOE.gguf)
- [Devstral-Small-2-24B](https://huggingface.co/unsloth/Devstral-Small-2-24B-Instruct-2512-GGUF?show_file_info=Devstral-Small-2-24B-Instruct-2512-Q4_K_M.gguf)


# Step 1: Start Router Mode
## Simple router mode start

```
llama-server --models-dir C:\AI\Models --port 8080
```

Then visit http://localhost:8080/. The important part is that it exposes an OpenAI-style API under `/v1`.
## If you want per-model presets

Use a preset file like `models.ini` when you want different context sizes, temps, or GPU settings per model.

```
version = 1

[*]
ngl = 99

[Qwen3.6-27B]
model = C:\AI\Models\Qwen3.6-27B-Q4_K_M.gguf

[Qwen3.6-35B-A3B]
model = C:\AI\Models\Qwen3.6-35B-A3B-UD-Q4_K_M.gguf

[Gemma3-27B]
model = C:\AI\Models\gemma-3-27b-it-Q4_K_M.gguf

[GPT-OSS-20B]
model = C:\AI\Models\gpt-oss-20b-MXFP4_MOE.gguf
```

```bash
llama-server --models-preset C:\AI\Models\models.ini --host 0.0.0.0 --port 8080
```

# Step 2: Point LiteLLM at it

In your LiteLLM config, use an OpenAI-style entry like this:

```yaml
model_list:
  # === LOCAL MODELS ===
  # Rank 1: local/Qwen3.6-27B
  # Best overall daily-driver model for your 3090.
  # Strong balance of intelligence, fit, and speed.
  - model_name: Qwen3.6-27B
    litellm_params:
      model: openai/Qwen3.6-27B
      api_base: http://192.168.1.149:8080/v1
      api_key: fake-key

  # Rank 2: local/Qwen3.6-35B-A3B
  # Heavier, stronger fallback for deeper reasoning.
  # Use when you want more capability and can spare the memory.
  - model_name: Qwen3.6-35B-A3B
    litellm_params:
      model: openai/Qwen3.6-35B-A3B
      api_base: http://192.168.1.149:8080/v1
      api_key: fake-key

  # Rank 3: local/Gemma3-27B
  # Good alternate general-purpose model.
  # Nice for varied response style and strong instruction following.
  - model_name: Gemma3-27B
    litellm_params:
      model: openai/Gemma3-27B
      api_base: http://192.168.1.149:8080/v1
      api_key: fake-key

  # Rank 4: local/GPT-OSS-20B
  # Lightweight, faster fallback.
  # Best when you want lower VRAM pressure and quicker responses.
  - model_name: GPT-OSS-20B
    litellm_params:
      model: openai/GPT-OSS-20B
      api_base: http://192.168.1.149:8080/v1
      api_key: fake-key
```

LiteLLM’s docs show that for OpenAI-compatible backends, you use `openai/` in the model name and the backend’s `/v1` base URL.[docs.litellm](https://docs.litellm.ai/docs/providers/openai_compatible)

# Step 3: Start llama-server at boot

Create a bat file:

```powershell
powershell -NoProfile -Command "@'
@echo off
cd /d ""C:\Program Files\llamacpp""
start """" llama-server.exe --models-preset C:\AI\Models\models.ini --host 0.0.0.0 --port 8080
'@ | Set-Content -Encoding ASCII C:\AI\start-llama-server.bat"
```

Register the task scheduler:

```powershell
$action = New-ScheduledTaskAction -Execute "C:\AI\start-llama-server.bat"
$trigger = New-ScheduledTaskTrigger -AtStartup
$principal = New-ScheduledTaskPrincipal -UserId "SYSTEM" -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -StartWhenAvailable -RestartCount 3 -RestartInterval (New-TimeSpan -Minutes 1)

Register-ScheduledTask `
  -TaskName "LlamaServer" `
  -Action $action `
  -Trigger $trigger `
  -Principal $principal `
  -Settings $settings `
  -Description "Start llama-server at boot"
```

If you want, I can give you a ready-to-paste **Windows config** for LiteLLM plus the exact `llama-server` command for your Qwen model.

---
[^1]: [Install Llama.cpp on Windows 11 & Run AI Locally for Free](https://www.youtube.com/watch?v=dJi_IkIeo5w&t=1s)
