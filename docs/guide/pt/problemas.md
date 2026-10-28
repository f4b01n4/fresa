# Resolução de problemas

| Sintoma | Causa e solução |
|---|---|
| A máquina deixa de responder depois de mexer no `config.yaml` | O FluidNC não aceita comentários na mesma linha dos valores. Liga por USB, envia `$SS` para ver os erros, depois `$Config/Filename=<ficheiro anterior>` e `$Bye`. |
| "No SD card" | O cartão está em exFAT. Formata em FAT32 (MS-DOS FAT, Master Boot Record no macOS). |
| Isolamento limpo nalgumas zonas e só riscado noutras | A placa verga ou mexeu. Cola-a em toda a área, volta a sondar, usa **Retocar zona**. |
| ALARM:14 | A máquina precisa de homing (`$H`). |
| ALARM:5 a sondar | Nada tocou dentro da distância de procura: pinça fora do cobre, ou o ponto está numa ilha de cobre isolada. |
| Trackpad errático com USB | Fuga para a terra pela fonte da CNC; usa a ligação por rede. |
| Amplitude do mapa acima de 0,3 mm | A placa não está assente na base; fixa-a melhor antes de cortar. |
| Pads e pistas saem muito mais estreitos do que o desenho, alguns cortados, mesmo com a placa plana | O sulco é mais largo do que a app pensa: a excentricidade do spindle ou da pinça faz uma V-bit «de 0,1 mm» cortar 0,3–0,5 mm. Corre `fixtures/calibration/vbit-grooves.nc` numa zona livre de cobre (zero XY aí, Z com a sonda), mede os 6 sulcos ao microscópio e põe a largura do mais raso como **diâmetro da ponta** dessa V-bit em Ferramentas…. Baixa a profundidade para 0,05 mm. Os intervalos mais estreitos do que o corte real passam a ser cortados a meio (o Resultado lista-os). Limpa e volta a apertar a pinça; uma V-bit cónica de 2–4 gumes roda mais certa do que uma de um gume em «D». |
