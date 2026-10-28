# Painéis, limpeza de cobre, verificação de furos e desgaste

## Painel (várias cópias)
**Parâmetros do trabalho → Painel (cópias)**: indica colunas e linhas. Todos os
programas (isolação, limpeza, furos, recorte) abrangem todas as cópias; a
grelha de sondagem cobre o painel inteiro. O espaço entre placas tem de ser
pelo menos o diâmetro da fresa de recorte + 2 mm, senão os recortes tocam-se (o
Fresa avisa). Cada cópia mantém as suas pontes.

## Limpeza de cobre
A **Limpeza de cobre** remove o cobre que não faz parte de nenhuma pista,
depois da isolação (`clearing.nc`, logo a seguir a `isolation.nc`). A
ferramenta de limpeza mantém o seu bordo a meia largura de isolação do cobre,
para sobrepor o sulco da isolação sem tocar nas pistas.

- Usa uma fresa de 1 mm ou maior: limpar uma placa inteira demora muito mais
  do que a isolação (a pré-visualização mostra o tempo).
- **Só junto ao cobre** limpa uma faixa da largura escolhida à volta do cobre
  em vez da placa toda — mais rápido e normalmente suficiente para soldar.
- O passo lateral está limitado a 50 % para não ficar nenhuma tira por cortar.
- É nivelada com o mapa de alturas, tal como a isolação.

## Verificação de furos
Antes de cortar, o Fresa compara o ficheiro de furação com a placa e lista os
problemas em **Avisos** (quadrados âmbar na pré-visualização):
- dois furos com os bordos a menos de 0,2 mm (a parede entre eles parte);
- um furo a menos de 0,3 mm do bordo da placa;
- um pad furado com menos de 0,15 mm de anel de cobre.

## Imagens e desgaste das ferramentas
As ferramentas são desenhadas a partir das suas medidas junto a cada escolha
de ferramenta, na biblioteca e na checklist (os V-bits mostram a largura de
corte à profundidade escolhida).

Cada ferramenta da biblioteca conta o que já cortou: metros para V-bits e
fresas, furos para brocas. A contagem sobe quando um trabalho termina (ou pela
parte feita, quando é parado). Se o Fresa não souber que ferramenta da
biblioteca foi usada, pergunta. A barra fica âmbar aos 80 % da vida esperada e
vermelha aos 100 %; a checklist também avisa. Depois de montar uma ferramenta
nova, abre **Ferramentas…** e carrega em **Repor (ferramenta nova)**. A vida
esperada é editável por ferramenta (por omissão: V-bit 30 m, fresa 50 m, broca
300 furos em FR4).
