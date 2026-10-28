# Ligar a máquina

O Fresa fala com controladores **GRBL 1.1**, **grblHAL**, **FluidNC** e
**Marlin** e deteta qual está ligado (envia `$I` e depois `M115`). Abre o
separador **Máquina**.

| Firmware | Cartão | Como os ficheiros chegam ao cartão | Ajustes ao vivo | Editor de definições |
|---|---|---|---|---|
| FluidNC | sim | rede (WebDAV) | sim | sim (novo ficheiro de configuração + reinício) |
| grblHAL | se a placa tiver | — | sim | sim (definições `$`) |
| GRBL 1.1 | não | — (streaming a partir da app) | sim | sim (definições `$`) |
| Marlin | se a placa tiver | pelo cabo (M28) | não | sim (M92/M203/M201 + M500) |

Sem cartão, os trabalhos são enviados em **streaming** a partir da aplicação,
linha a linha: mantém o computador ligado e sem suspender até ao fim.

## Rede (Telnet) — recomendado para FluidNC
Tipo: **Rede (Telnet, porta 23)**, endereço: o IP do controlador (aparece na
WebUI) ou `fluidnc.local`. Carrega em **Ligar**. Devem aparecer o firmware e o
nome da máquina por baixo dos botões, e as posições a atualizar.

## USB série
Tipo: **USB série**, escolhe a porta (`/dev/cu.usbserial-…` no macOS, `COM3` no
Windows). Se o trackpad do Mac ficar errático com o cabo USB ligado, a fonte da
CNC está a fugir para a terra pelo USB: usa a ligação por rede, o carregador do
Mac com terra (três pinos) ou um isolador USB.

## Primeiras verificações
1. **Homing** (precisa de fins de curso).
2. Encosta as duas pinças da sonda: a linha **Sonda** tem de dizer
   **EM CONTACTO**.
3. Move com as setas; confirma que +X leva o spindle para a direita, +Y afasta-o
   de ti, −Z desce.

## Que máquina é?
Depois de ligar, o Fresa mostra o firmware que encontrou e, se ainda não
escolheste uma máquina, sugere perfis compatíveis da **biblioteca de máquinas**
(**Máquinas…**). Ao escolher um, o curso da máquina passa a ser usado para
verificar se os trabalhos cabem. Os perfis incluídos indicam de onde vêm os
valores; só os marcados como confirmados foram medidos numa máquina real. Usa
**Criar a minha** para copiar um perfil e editá-lo; as tuas máquinas ficam
gravadas na pasta de dados da aplicação e podem ser exportadas/importadas.

## Definições da máquina
**Definições da máquina…** lê as definições do controlador para um formulário
igual em todos os firmwares: passos/mm, velocidade máxima, aceleração, curso,
sentido dos motores, homing, limites, gama do spindle, entrada da sonda. Os
campos alterados ficam realçados; **Aplicar** mostra primeiro a lista de
alterações. Antes de escrever o que quer que seja, o Fresa grava uma cópia das
definições atuais na pasta `machine-backups` dos dados da aplicação.

- **GRBL / grblHAL / Marlin**: as alterações são escritas de imediato (no
  Marlin também ficam guardadas com `M500`).
- **FluidNC**: o Fresa escreve um *novo* ficheiro de configuração
  (`fresa-<data>.yaml`) no controlador e seleciona-o. Carrega em **Reiniciar o
  controlador agora**: o Fresa reinicia-o, volta a ligar e confirma que arrancou
  com o novo ficheiro. Se não arrancou (erro no ficheiro), **Usar configuração
  anterior** volta a selecionar a antiga. O teu `config.yaml` original nunca é
  substituído.

Na mesma janela há duas ajudas:
- **Calibrar passos/mm**: desloca uma distância conhecida, mede o que a máquina
  andou de facto e o Fresa calcula o valor corrigido.
- **Verificar o sentido dos motores**: desloca cada eixo um pouco em +; se foi
  para o lado errado, um clique inverte esse motor.

## O cartão SD
Formata-o em **FAT32** (cartões acima de 32 GB vêm em exFAT e não são lidos).
Na secção **Cartão e execução**, indica o endereço HTTP do controlador e usa **Enviar**
para mandar os ficheiros; o Fresa confirma os tamanhos com `$SD/List`.

## Simulador
Escolhe **Simulador** para experimentar tudo sem máquina, e escolhe o firmware
que ele imita (FluidNC, GRBL 1.1, grblHAL ou Marlin).
