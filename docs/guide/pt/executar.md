# Executar um trabalho

## Antes de cada execução: a checklist
**Executar** abre uma checklist. O Fresa verifica o que consegue (homing nesta
sessão, zero de trabalho definido, Z zerado com a sonda há pouco, mapa de alturas
aplicado e a sua amplitude, percursos dentro do curso da máquina, pinça da sonda
retirada, o ficheiro no cartão é o que exportaste) e pede-te que marques o resto
(a ferramenta montada, a porca da pinça, o spindle). Itens a vermelho precisam de
um segundo clique para executar mesmo assim.

## Durante o trabalho
- A **pré-visualização** mostra a fresa ao vivo (cor = estado da máquina) com um
  rasto curto; os percursos já cortados ficam verdes e o atual amarelo.
  **Seguir a fresa** mantém-na à vista.
- O separador **Máquina** mostra a percentagem, o percurso atual, o tempo
  decorrido e o que falta (corrigido pelo ritmo real depois do primeiro minuto).
- **Overrides**: avanço e rotação ±10 % (100 % repõe), rápidos 25/50/100 %.
  Atuam logo, sem parar o trabalho.
- Trabalhos arrancados pela WebUI ou pelo ecrã do controlador também são
  seguidos quando o nome do ficheiro coincide com um do projeto aberto.

## Parar e retomar
**Parar trabalho** pausa e faz reset ao controlador. O Fresa lembra-se do
percurso onde parou: *Retomar no percurso* → **Criar o ficheiro de retoma** cria
o `…-resume-N.nc` (mesma ferramenta e parâmetros, a começar no percurso N). Faz
homing, confirma o zero, envia-o e executa-o. Um alarme ou uma ligação perdida
durante o trabalho ficam registados da mesma forma.

## Desligar e continuar no dia seguinte
O Fresa guarda o zero de trabalho (G54), a referência do Z e onde o trabalho
parou no `fresa.json` do projeto. No dia seguinte: liga, **Homing**, e na caixa
*Sessão guardada* **Verificar o zero guardado** (o controlador costuma mantê-lo)
ou **Repor o zero guardado**, e **Verificar o Z na referência** (um toque da
sonda: se ler mais de 0,05 mm de diferença, a placa ou a ferramenta mexeram —
zera o Z outra vez). Precisa de fins de curso; sem eles, marca a posição antes
de desligar.

## Verificar o mapa
Antes de um isolamento longo, **Verificar mapa** volta a sondar os quatro cantos
e o centro e compara com o mapa; mais de 0,1 mm de diferença pede nova sondagem.

## Mover com o teclado e a régua
Liga *Mover com o teclado*: setas movem X/Y, Page Up/Down movem Z, `[` e `]`
mudam o passo, Esc pára. **Medir** na barra da pré-visualização: arrasta para
obter a distância, ΔX, ΔY e o ângulo (agarra os centros dos furos).
