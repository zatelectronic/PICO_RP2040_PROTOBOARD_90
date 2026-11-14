# PICO_PROTOBOARD_90 — R02 (2026-11-13)

Revisão de **qualidade e didática**. Cobre (trilhas, pads, zona) **igual ao R01** — nenhuma mudança elétrica.

## PCB
1. **Cantos arredondados** r = 1 mm (cobre–borda continua 2,0 mm).
2. Frente: **colchetes de grupo** acima dos nomes — `GPIO 0-15 · 3,3 V`, `GPIO 16-22`, `RST`, `ADC 0-2`, `ENERGIA`.
3. Frente: os 8 **GND em caixa** (achados de relance).
4. Verso: **tabela de funções alternativas** de GP0–GP22 e GP26–GP28 (UART · I2C · SPI · PWM · ADC), em ordem de leitura de quem olha o verso.
5. Verso: identificação movida para entre as fileiras do Pico + avisos `lógica 3,3 V · NÃO tolera 5 V` e lista dos GND.
6. Revisão R02 na serigrafia e no title block.

## Esquemático
1. **Função de cada pino ao lado do global label** (PICO e BARRA_90), em coluna alinhada e com cor por tipo: azul = GPIO, verde = ADC, vermelho = alimentação, laranja = controle.
2. Legenda de cores na folha PICO.
3. Campos Reference/Value reposicionados pelo verificador `schtext.py` (padrão doc 03 §Textos): colados ao corpo, 1,27 mm, horizontais, sem sobreposição.
4. PWR_FLAG do GND movido para um T próprio (eliminada junção de 4 vias).

## Conferências
- ERC simulado 0 · esquema × PCB 0 diferenças (33 nets) · `schtext check` 0 apontamentos
- Serigrafia frente e verso: 0 sobreposição, 0 sobre pad (folga 0,15 mm), 0 fora da placa
- Cobre–borda mín. 2,025 mm · arquivos íntegros (parênteses/aspas)

## Fazer no KiCad
1. Abrir PCB → **B** (preencher zona) → **DRC**; esquema → **ERC**. Esperado 0/0.
2. Ver o verso em 3D (tabela legível; texto mínimo 0,8 mm).
