# Como configurar o VS Code e usar Rust em diferentes distribuições Linux

Este guia descreve como instalar o Visual Studio Code (VS Code) e configurar o Rust em três distribuições populares de Linux: **Arch Linux**, **NixOS** e **Fedora**.

## Instalar o VS Code

### **Arch Linux (e derivados como EndeavourOS, CachyOS ou Manjaro)**
No Arch Linux, o VS Code pode ser facilmente instalado a partir do AUR (Arch User Repository).
```bash
sudo yay -S visual-studio-code-bin
```
Se não tive yay, instalar isso:
```bash
sudo pacman -Syu
sudo pacman -S yay
sudo yay -S visual-studio-code-bin
```

### **Fedora**
```bash
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo
sudo dnf check-update
sudo dnf install code
code .
```
### ***NixOS***
Edite seu arquivo de configuração configuration.nix, procurar environment.systemPackages = with pkgs;, adicione dentro "vscode"
```bash
environment.systemPackages = with pkgs; [
  vscode
];
```
Rebuild o sistema:
```bash
sudo nixos-rebuild switch
```
## Para começar a programar em Rust, Crie um novo projeto Rust
```bash
cargo new hello_world
cd hello_world
code .
```

## ⚠️ Problemas comuns

Fedora: Se você não consegue abrir o VS Code após a instalação, certifique-se de que o Flatpak não está interferindo. Use a instalação via repositório oficial da Microsoft.

Arch Linux: Deve instala o vscode pelo yay e não pacman!
