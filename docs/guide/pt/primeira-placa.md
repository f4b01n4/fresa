# A primeira placa

## 1. Exportar do KiCad
Plot → Gerber, formato X2, mm. Camadas **F.Cu** e **Edge.Cuts**. Gerar a
furação Excellon em mm (decimal). Gerar também o ficheiro de trabalho
(`.gbrjob`): dá a espessura da placa.

## 2. Abrir a pasta
**Abrir pasta…** e confirmar que cada ficheiro tem o papel certo.

## 3. Parâmetros
- **Material** e **Ferramentas…** (a biblioteca) dão avanços sensatos.
- Atenção à **Largura de corte**: tem de caber entre os pads mais próximos. Se o
  painel de resultado mostrar o aviso vermelho "a ferramenta não cabe", reduz a
  profundidade ou usa uma V-bit mais fechada. Clica num aviso para ir lá.

## 4. Fixar a placa plana
Cola-a com fita dupla face em **toda** a área, numa base plana (Máquina →
*Facejar a base* aplaina uma). Uma placa que verga com a sonda não se nivela.

## 5. Zerar e sondar
Separador Máquina: **Homing**, leva a fresa ao canto inferior esquerdo da placa
1–2 mm acima do cobre, **Zero XY aqui**, pinça no cobre e fio na fresa,
**Zerar Z com a sonda**, depois **Sondar grelha**. A amplitude deve ficar abaixo
de 0,3 mm; acima disso, fixa melhor a placa.

## 6. Cortar
Com **Aplicar ao exportar** ligado, **Envia** os ficheiros e **Executa-os** um a
um: isolamento, furação, furos fresados, recorte. Depois de cada troca de
ferramenta, **Zerar Z com a sonda** outra vez (ou usa o
[ficheiro único](ficheiro-unico.md)).

## 7. Se uma zona ficou rasa
Na pré-visualização, **Retocar zona**, arrasta um retângulo por cima e corre o
`isolation-retoque.nc`: só essa zona, um pouco mais fundo.
