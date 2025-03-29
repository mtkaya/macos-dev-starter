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

bash
git clone https://github.com/kullaniciadi/macos-dev-starter.git
cd macos-dev-starter
chmod +x setup.sh
./setup.sh


## ⚙️ Setup.sh Kurulumu

#!/bin/bash

# MacOS Python AI Geliştirici Ortamı Kurulum Scripti
# Bu script Homebrew, pyenv, VS Code, Python paketleri ve temel AI tool'larını kurar

# 1. Homebrew kurulumu
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Gerekli brew paketleri
brew install pyenv pyenv-virtualenv git wget
brew install --cask iterm2 visual-studio-code docker postman

# 3. Python kurulumu ve ortam ayarı
pyenv install 3.11.6
pyenv virtualenv 3.11.6 dev-env
pyenv activate dev-env

echo 'eval "$(pyenv init --path)"' >> ~/.zprofile

echo "[INFO] Python ortamı ayarlandı."

# 4. VS Code uzantıları
echo "[INFO] VS Code uzantıları yükleniyor..."
code --install-extension ms-python.python
code --install-extension ms-toolsai.jupyter
code --install-extension GitHub.copilot

# 5. Python AI requirements.txt oluşturma
cat <<EOF > requirements.txt
numpy
pandas
matplotlib
scikit-learn
jupyterlab
transformers
torch
torchaudio
torchvision
sentence-transformers
langchain
llama-index
openai
peft
bitsandbytes
accelerate
EOF

# 6. requirements yükleniyor
echo "[INFO] Python paketleri yükleniyor..."
pip install -r requirements.txt

# 7. Test kodu oluşturma
cat <<EOF > llm_test.py
import torch
from transformers import pipeline

device = 0 if torch.cuda.is_available() else -1
print(f"Kullanılan cihaz: {'GPU' if device == 0 else 'CPU'}")

classifier = pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english", device=device)

text = "I love using AI tools. They make my life easier!"
result = classifier(text)[0]

print("Girdi:", text)
print("Tahmin:", result['label'])
print("Güven:", round(result['score'] * 100, 2), "%")
EOF

# 8. Tamamlandı
echo "[TAMAMLANDI] Ortam kuruldu. llm_test.py dosyası ile test edebilirsin."
