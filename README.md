# imk-dev-tool

`imk-dev-tool` est un utilitaire CLI multi-plateforme conçu pour accélérer la configuration d’environnements de développement et automatiser certaines tâches.

Ce guide contient :

- Installation pour Linux  
- Installation pour macOS  
- Installation pour Windows  
- Script d’installation automatique `install.sh`  
- Commandes de test  

---

# 🚀 Installation

Téléchargez et installez le binaire correspondant à votre système d'exploitation.

---

# 🐧 Linux

### 1️⃣ Télécharger le binaire
```bash
wget https://github.com/ywoume/imk-starterkit/releases/download/0.0.8/imk-dev-tool-linux-amd64 -O imk-dev-tool
```

### 2️⃣ Rendre exécutable
```bash
chmod +x imk-dev-tool
```

### 3️⃣ Installer dans `/usr/local/bin`
```bash
sudo mv imk-dev-tool /usr/local/bin/imk
```

### 4️⃣ Vérification
```bash
imk --version
```

---

# 🍏 macOS (Apple Silicon – M1 / M2 / M3)

### 1️⃣ Télécharger
```bash
curl -L https://github.com/ywoume/imk-starterkit/releases/download/0.0.8/imk-dev-tool-macos-arm64 -o imk-dev-tool
```

### 2️⃣ Rendre exécutable
```bash
chmod +x imk-dev-tool
```

### 3️⃣ Installer
```bash
sudo mv imk-dev-tool /usr/local/bin/imk
```

### 4️⃣ Vérification
```bash
imk --version
```

### ⚠️ macOS peut bloquer l’exécution :
```bash
xattr -d com.apple.quarantine /usr/local/bin/imk
```

---

# 🏁 Windows (PowerShell)

### 1️⃣ Télécharger
```powershell
Invoke-WebRequest -Uri "https://github.com/ywoume/imk-starterkit/releases/download/0.0.8/imk-dev-tool-windows-amd64.exe" -OutFile "imk.exe"
```

### 2️⃣ Ajouter au PATH
```powershell
Move-Item imk.exe "C:\Windows\System32\imk.exe"
```

### 3️⃣ Vérification
```powershell
imk --version
```

---

# 🔄 Mise à jour

Supprimer l’ancien binaire :

```bash
sudo rm /usr/local/bin/imk
```

Puis refaire l’installation selon votre OS.

---

# 🔧 Installation automatique (Linux / macOS)

```bash
curl -fsSL https://raw.githubusercontent.com/ywoume/imk-starterkit/main/install.sh | bash
```

OU utilisez directement le script ci-dessous.

---

# 📜 Script `install.sh`

```bash
#!/bin/bash

set -e

VERSION="0.0.8"
REPO="https://github.com/ywoume/imk-starterkit/releases/download/$VERSION"

GREEN="\e[32m"
NC="\e[0m"

echo -e "${GREEN}🌍 Détection de l’OS...${NC}"

case "$(uname -s)" in
    Linux*)
        FILE="imk-dev-tool-linux-amd64"
        ;;
    Darwin*)
        FILE="imk-dev-tool-macos-arm64"
        ;;
    *)
        echo "❌ OS non supporté automatiquement."
        echo "Téléchargez le binaire manuellement depuis :"
        echo "$REPO"
        exit 1
        ;;
esac

echo -e "${GREEN}⬇️ Téléchargement du binaire : $FILE${NC}"

curl -L "$REPO/$FILE" -o imk
chmod +x imk

echo -e "${GREEN}📦 Installation dans /usr/local/bin...${NC}"

sudo mv imk /usr/local/bin/imk

echo -e "${GREEN}✔ Installation terminée !${NC}"
echo "Version installée :"
imk --version
```

Pour exécuter le script :

```bash
bash install.sh
```

---

# 🧪 Tester l'installation

```bash
imk --help
```

---

# 🐞 Support / Issues

👉 https://github.com/ywoume/imk-starterkit/issues

---

# 🎉 Merci d’utiliser imk-dev-tool !
