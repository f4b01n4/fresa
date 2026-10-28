# Relevo 3D (STL e imagens)

A área de trabalho **Relevo 3D** esculpe um relevo — uma placa, um medalhão, um
mapa topográfico, uma imagem em relevo — a partir de um **modelo STL** ou de
uma **imagem PNG/JPG**: desbaste com uma fresa plana e acabamento com uma fresa
de ponta esférica.

## 1. Abrir o modelo
- **STL** (binário ou ASCII; Printables, Thingiverse, o teu CAD): o Fresa
  olha para ele de cima. Roda-o em passos de 90° em X, Y ou Z até o lado que
  queres ficar para cima; define a escala (100 % = unidades do ficheiro como mm;
  **Ficheiro em polegadas** para modelos em polegadas) ou **Ajustar ao
  material**.
- **Imagem**: as partes claras ficam altas e as escuras são cortadas mais fundo
  (**Escuro = alto** inverte). Define a largura e a profundidade do preto; a
  gama dá forma à curva e a suavização tira o ruído do JPEG.

Depois coloca-o no material e escolhe a que distância do topo do material fica
o ponto mais alto (0 = encostado ao topo). **Detalhe** é a grelha onde a
superfície é amostrada (0,1 mm serve para uma esfera de 3 mm; mais fino é mais
lento).

## 2. Material e área
Material (os avanços vêm da biblioteca de ferramentas), tamanho, espessura, Z0
(topo do material ou mesa de sacrifício). **Área a cortar**: o retângulo
inteiro do relevo, ou só a silhueta do modelo (mais uma margem), deixando o
material à volta intacto.

## 3. Desbaste e acabamento
- **Desbaste** (fresa plana): retira material em níveis de Z do passo vertical,
  esvaziando cada nível com passes concêntricos, e para um pouco acima da
  superfície final (**Deixar para o acabamento**, 0,3 mm por omissão). Nunca
  corta essa pele.
- **Acabamento** (fresa de ponta esférica — acrescenta uma em
  **Ferramentas…** com **Ponta esférica** marcado): passes paralelos em X, em Y
  ou nos dois; o passo lateral resulta da **altura da crista** que aceitas
  entre passes (0,02 mm fica liso em madeira). A ferramenta segue a superfície
  exatamente onde a consegue alcançar (o raio da esfera limita quão aguda pode
  ser uma cavidade).

Programas: `relief-roughing.nc` e `relief-finishing.nc`. Relevos grandes levam
alguns segundos a calcular — o progresso aparece por baixo da
pré-visualização, com **Cancelar**.

## 4. Cortar
Como em todas as áreas de trabalho: **Resultado** grava os ficheiros junto ao
modelo, o separador **Máquina** executa-os (cartão ou streaming, checklist,
progresso, parar e retomar, desgaste). Os relevos 3D **não são nivelados** com
mapa de alturas: faceja primeiro o topo do material (**Máquina → Facejar**)
para o Z0 ficar plano. As definições ficam gravadas junto ao modelo em
`<nome>.relief.fresa.json`.
