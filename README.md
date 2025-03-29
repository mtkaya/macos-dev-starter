# 🧠 macOS Developer Starter Kit
A macOS development starter kit for Python, AI, and LLM projects. Includes setup script, environment tools, and test code.



Bu repo, Python ve AI/LLM (Large Language Model) geliştirme yapan geliştiriciler için **macOS ortamına özel** hazırlanmış bir başlangıç setidir. Amacı, hem Anaconda hem de Visual Studio Code ile uyumlu, GPU/CPU fark etmeksizin çalışan bir temel geliştirme ortamı sunmaktır.

## 🚀 Neler İçerir?

- Homebrew ile temel yazılımların kurulumu
- Pyenv ile Python ortamının yönetimi
- VS Code eklentilerinin kurulumu
- AI ve LLM projeleri için geniş `requirements.txt`
- HuggingFace + Transformers destekli LLM test kodu (`llm_test.py`)
- Terminal üzerinden tek komutla çalışan `setup.sh` script’i

## ⚙️ Kurulum

```bash
git clone https://github.com/kullaniciadi/macos-dev-starter.git
cd macos-dev-starter
chmod +x setup.sh
./setup.sh

