# Fresa

**CAM e controlo de máquina para fresadoras CNC amadoras** — fresagem de PCBs
por isolação com nivelamento por sonda, corte e gravação a partir de DXF/SVG, e
relevos 3D a partir de modelos STL e imagens. Fala com GRBL 1.1, grblHAL,
FluidNC e Marlin.

[English](README.md)

## Descarregar

Vai a **[Releases](../../releases/latest)** e escolhe o ficheiro do teu sistema:

| Sistema | Ficheiro | Atualizações |
|---|---|---|
| macOS 11+ (Intel e Apple silicon) | `Fresa_<versão>_universal.dmg` | na aplicação |
| Windows 10/11 | `Fresa_<versão>_x64-setup.exe` (ou `.msi`) | na aplicação (setup.exe) |
| Linux | `Fresa_<versão>_amd64.AppImage` (ou `.deb`) | na aplicação (AppImage) |

Depois de instalado, o Fresa procura novas versões sozinho e instala-as com um
clique (Definições → Atualizações) — não é preciso voltar a descarregar.

## Primeira utilização

- **macOS**: o Fresa não é assinado pela Apple. Abre-o uma vez, fecha o aviso e
  vai a Definições do Sistema → Privacidade e segurança → **Abrir mesmo assim**
  (ou `xattr -dr com.apple.quarantine /Applications/Fresa.app`).
- **Windows**: o SmartScreen pode dizer "O Windows protegeu o seu PC": **Mais
  informações → Executar mesmo assim** (o instalador não é assinado).
- **Linux**: `chmod +x Fresa_*.AppImage` e executa-o. Para acesso à porta série
  USB, junta-te uma vez ao grupo `dialout`: `sudo usermod -aG dialout $USER`, e
  volta a iniciar a sessão.

## O que faz

- **PCB**: Gerber/Excellon do KiCad à entrada, G-code de isolação / furação /
  recorte à saída; verificação de encaixe da ferramenta, limpeza de cobre,
  painéis, placas de dupla face, mapa de alturas por sonda para placas
  empenadas.
- **Corte e gravação**: DXF e SVG; contornos com pontes, caixas, gravação,
  V-carve, furação, para madeira, MDF, acrílico e alumínio.
- **Relevo 3D**: modelos STL e imagens; desbaste e acabamento com fresa
  esférica.
- **Máquina**: ligação por USB ou rede, deteção do firmware, deslocar, zerar,
  sondar, executar do cartão SD ou em streaming, progresso ao vivo, parar e
  retomar, editor das definições da máquina, biblioteca de ferramentas com
  contador de desgaste. Inglês e português europeu.

Este repositório só contém as versões publicadas. O código-fonte não é público.

© 2026 Fresa. Os binários são gratuitos para descarregar e usar; ver [LICENSE](LICENSE).
