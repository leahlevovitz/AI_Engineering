# 🧪 Prompt Engineering Lab: Natural Language → Windows CLI

> An iterative prompt-engineering project: turning plain-English requests into **safe, correct Windows CMD commands**, and improving the system prompt version by version.

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Groq](https://img.shields.io/badge/LLM-Groq_API-F55036)
![Gradio](https://img.shields.io/badge/UI-Gradio-FF7C00)
![Prompt Engineering](https://img.shields.io/badge/Prompt-Engineering-2DD4BF)

## 🎯 The challenge
LLMs are great at writing shell commands, and also great at writing **dangerous**, wrong or Linux-only ones.
The goal: a system prompt that makes the model return **exactly one valid Windows command**, or refuse safely.

## 🔁 Five prompt versions
The `prompts/` folder holds the full evolution of the system prompt, from a one-liner to a strict protocol:

| Version | What changed |
|---|---|
| `prompt-v_1` | Basic instruction: "return a Windows command" |
| `prompt-v_2` | Output format rules: command only, no markdown, no explanations |
| `prompt-v_3` | Windows-only syntax; no Unix tools like `head` or `grep` |
| `prompt-v_4` | **Safety rules**: block system folders, `format`, `shutdown`, destructive deletes |
| `prompt-v_5` | Step-by-step **mandatory protocol**: disqualification and safety check first, then generation |

Each version was tested against the same set of requests, and failures were documented (see the error log linked below) to drive the next iteration.

## ✨ Highlights
- **Prompt versioning**: prompts live in files, not in code, so they can be compared and swapped instantly.
- **Safety-first design**: unsafe requests return `WARNING: Unsafe command`; unsupported ones return `Unsupported`.
- **Gradio UI** for interactive testing of every prompt version.
- **Groq API** (OpenAI-compatible client) for fast inference.

## 🚀 Getting started
```bash
uv sync                      # or: pip install openai gradio python-dotenv
echo OPENAI_API_KEY=your_groq_key > .env
python app.py
```

## 📎 Documentation
- [Error documentation](https://drive.google.com/file/d/1RE6Hg78zlzCr1Qyyj2zR5iH6tzFVplKa/view?usp=drive_link)
- [Test results sheet](https://drive.google.com/file/d/1fs5TwF5Vr-7RGv-ohvH_cq1Z0Uvz3CEX/view?usp=drive_link)

> 🔗 See also **[WinCmd-Agent](https://github.com/leahlevovitz/WinCmd-Agent)**: the same idea running fully locally with Ollama.

---
👩‍💻 Built by **Leah Levovitz** · [LinkedIn](https://www.linkedin.com/in/leahlevovitz) · [GitHub](https://github.com/leahlevovitz)
