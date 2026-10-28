# Corte e gravação (DXF e SVG)

A área de trabalho **Corte e gravação** (barra de cima) transforma um desenho
2D em programas para madeira, MDF, acrílico ou alumínio leve: recortar peças,
caixas, gravação, V-carve e furação.

## 1. Abrir o desenho
**Abrir DXF/SVG…**. Suportado:
- **DXF** (LibreCAD, FreeCAD, Fusion, AutoCAD, QCAD…): linhas, arcos,
  círculos, polilinhas (com arcos), splines, elipses e blocos. As unidades vêm
  do ficheiro; se não as indicar, escolhe mm ou polegada. Os segmentos soltos
  são unidos em formas fechadas automaticamente (pontas a menos de 0,01 mm).
- **SVG** (Inkscape, Illustrator…): caminhos, retângulos, círculos, elipses,
  linhas, polígonos, grupos e transformações. Tamanhos em mm/cm/in são exatos;
  tamanhos em píxeis precisam do DPI certo (96 para Inkscape e browsers, 72 para
  ficheiros antigos do Illustrator). As camadas do Inkscape passam a camadas.
- **O texto não é importado**: converte-o primeiro em curvas (Inkscape:
  Caminho → Objeto para caminho).

A lista de camadas mostra o que entrou; desmarca uma camada para a esconder.

## 2. Material
Material (madeira, MDF, acrílico, alumínio — os avanços vêm da biblioteca de
ferramentas para esse material e são **pontos de partida**: afina-os num
retalho), tamanho e espessura, onde fica o desenho em cima dele, onde é o X0 Y0
(canto do material, centro do material ou a origem do próprio desenho) e onde
é o Z0 (topo do material ou a mesa de sacrifício). Um desenho novo recebe um
material 10 mm maior do que ele a toda a volta.

## 3. Operações
Acrescenta operações com os botões; cada uma usa os traços das camadas
escolhidas, ou traços em que clicas na pré-visualização (**Escolher na
pré-visualização**, shift-clique acrescenta).

| Operação | O que faz |
|---|---|
| Contorno | Corta ao longo das formas: **por fora** (a peça), **por dentro** (um furo) ou **sobre a linha**, por passes de profundidade, com pontes, entrada em rampa, sentido concordante ou convencional, e sobre-espessura opcional |
| Caixa | Esvazia o interior das formas fechadas; formas dentro de formas ficam como ilhas; o passe da parede é o último |
| Gravar | Segue as linhas a uma profundidade (também linhas abertas) |
| V-carve | Esvazia formas fechadas com um V-bit a uma profundidade, para os bordos ficarem com o chanfro do V (o V-carve de profundidade variável vem mais tarde) |
| Furar | Fura os círculos (com broca) ou fresa-os em hélice (com fresa), filtrados por diâmetro |

Seja qual for a ordem da lista, os programas correm gravar → V-carve → furar →
caixa → contornos interiores → contornos exteriores, para a peça só se soltar
no fim. Cada operação é um ficheiro: `01-gravar.nc`, `02-contorno.nc`, ….

**Simular**, na pré-visualização, mostra o corte até um certo momento.

## 4. Cortar
O separador **Resultado** grava os ficheiros `.nc` junto ao desenho; o
separador **Máquina** funciona tal como para PCBs: cartão ou streaming,
checklist, progresso, parar e retomar, desgaste das ferramentas. As definições
ficam gravadas junto ao desenho em `<nome>.fresa.json`.

Em material irregular podes sondar um mapa de alturas (precisa de superfície
condutora ou de uma sonda) e marcar **Seguir o mapa de alturas**: todos os
programas passam a seguir a superfície.
