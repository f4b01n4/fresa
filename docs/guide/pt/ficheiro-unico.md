# Ficheiro único com trocas de ferramenta

Em **Resultado → Saída**, liga **Ficheiro único com trocas de ferramenta (M0)**.
O Fresa grava o `combined.nc` com todas as operações por ordem. Em cada troca:

1. O spindle pára e a máquina pausa com uma mensagem (*TROCA 1/2: …*).
2. Troca a ferramenta, deixa-a 1–10 mm acima do cobre deslizando-a na pinça,
   liga-lhe a pinça da sonda e **Retoma** (separador Máquina, ou a WebUI).
3. A ferramenta nova toca no cobre duas vezes (rápida, depois lenta) e o Z fica
   zerado.
4. Uma segunda pausa pede para tirares a pinça. **Retoma** outra vez: o spindle
   arranca e o corte continua.

O ponto de sonda é, por omissão, onde fizeste o primeiro zero Z. O Fresa avisa a
vermelho quando o ponto está numa ilha de cobre que o isolamento separa (a
pinça não veria o contacto), num rasgo ou num furo. Antes de confiar nele em
cobre, corre o ficheiro em modo de verificação (`$C`, depois
`$SD/Run=/combined.nc`, depois `$C`).
