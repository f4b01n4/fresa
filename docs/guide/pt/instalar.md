# Instalar

## macOS
1. Abre o `.dmg` e arrasta o **Fresa** para Aplicações.
2. O Fresa não está assinado pela Apple. Na primeira abertura:
   - **macOS 15 ou mais recente:** abre-o uma vez, fecha o aviso, depois
     Definições do Sistema → Privacidade e Segurança → **Abrir mesmo assim**.
     Ou no Terminal: `xattr -dr com.apple.quarantine /Applications/Fresa.app`
   - **macOS 14 ou anterior:** clique direito → Abrir → Abrir.
3. Carrega na engrenagem (canto superior direito) para escolher a língua.

## Windows
Executa `Fresa_<versão>_x64-setup.exe`. O SmartScreen pode dizer "O Windows
protegeu o seu PC": **Mais informações → Executar mesmo assim** (o instalador
não é assinado). As portas série USB aparecem como `COM3`, `COM4`… (instala o
controlador CH340/CP210x da tua placa se não aparecer nenhuma).

## Linux
Usa o **AppImage** (atualiza-se sozinho): `chmod +x Fresa_*.AppImage` e
executa-o. Também há um `.deb`, atualizado pelo gestor de pacotes. Para
acesso à porta série USB, junta-te uma vez ao grupo `dialout`:
`sudo usermod -aG dialout $USER`, e volta a iniciar a sessão.

## Vindo do pcbmill
A biblioteca de ferramentas é copiada no primeiro arranque. As pastas dos
projetos continuam a funcionar: o Fresa lê `pcbmill.json` e
`pcbmill.heightmap*.json` e passa a gravar `fresa.json` / `fresa.heightmap*.json`.

## Atualizações
O Fresa procura atualizações ao arrancar (Definições → Atualizações) e
instala-as no lugar com um clique — macOS, Windows (instalação pelo setup.exe) e
o AppImage de Linux. As atualizações são assinadas; o Fresa recusa qualquer
outra coisa.
