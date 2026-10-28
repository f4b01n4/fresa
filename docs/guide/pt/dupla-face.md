# Placas de dupla face

Precisa de F.Cu, B.Cu e Edge.Cuts. Liga **Dupla face** nos parâmetros.

- Dois pinos de alinhamento ficam na linha central horizontal da placa, por
  omissão fora dela (pino Ø 3,175 = encabadouro de uma fresa partida).
- A placa vira **da esquerda para a direita** (em torno de um eixo paralelo a
  Y). O Fresa espelha o fundo em torno do centro da placa, por isso os pinos
  caem nos mesmos furos e o zero XY não muda.
- Topo: isolamento, furação, furos fresados e `alignment.nc` (atravessa a placa e
  entra um pouco no martyr). Fundo: isolamento espelhado e recorte.
- Cada face tem o seu mapa de alturas: volta a sondar depois de virar.

O separador **Resultado** mostra o guia passo a passo com os números do teu
trabalho e o passo atual realçado.
