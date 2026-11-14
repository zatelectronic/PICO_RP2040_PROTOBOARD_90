# PICO_PROTOBOARD_90 — R03 (2026-11-13)

Base: arquivos do Kenneth (GP16 reroteado mais curto, DRC 0 / ERC 0). Cobre **não** foi alterado nesta revisão.

## Verso (B.SilkS) refeito
1. **Tabela de funções dos GPIO** em 2 blocos (GP0–GP12 e GP13–GP22, GP26–GP28) com **traços** (bordas, colunas e linhas), cabeçalho GPIO · UART · I2C · SPI · PWM; letra **1,0 mm** (era 0,8), linha de 1,8 mm.
2. **Tabela de alimentação/controle**: PINO · SINAL · FUNÇÃO para 40 VBUS, 39 VSYS, 37 3V3_EN, 36 3V3, 35 ADC_VREF, 30 RUN.
3. Quadro **ATENÇÃO · LÓGICA 3,3 V** (sem proteção, lista dos GND, pino n = pino n).
4. "Como ler" a tabela, marcação `< pino 40` / `pino 1 >` e "VISTA DE TRÁS".
5. Tudo escrito na ordem de leitura de quem olha o verso (texto espelhado correto).

## Outros
- Revisão R03 na serigrafia, title block e .kicad_pro.
- Net class **POWER** (VBUS, VSYS, 3V3, GND) agora por padrão de nome (`netclass_patterns`) — no arquivo recebido as atribuições estavam vazias.

## Conferências
- Serigrafia frente/verso: 0 sobreposição (cada item conferido separadamente), 0 sobre pad (folga 0,15 mm), 0 a menos de 0,4 mm da borda; tabela do verso não toca o contorno do Pico.
- Traços das tabelas não se cruzam (linhas horizontais quebradas nas colunas) → sem silk_overlap no DRC.
- Esquema × PCB: 0 diferenças (33 nets) · textos do esquema (schtext): 0.

## Fazer no KiCad
1. Abrir o PCB → **B** → **DRC** (esperado 0) → ver o verso em 3D (Alt+3, virar a placa).
2. Esquema → **ERC** (esperado 0).

## Correção do DRC (2026-11-13, 21h)
O DRC do Kenneth acusou 11 `silk_overlap` na tabela de alimentação do verso (linhas de 1,5 mm apertadas para textos com acento, cedilha e parênteses).
- Tabela PINO · SINAL · FUNÇÃO: cabeçalho 1,9 mm e linhas 1,66–1,72 mm, letra 0,9 mm, começando a 0,5 mm da borda e terminando antes do contorno do Pico.
- Textos sem parênteses: "5 V do USB · entrada/saída", "entrada 1,8 a 5,5 V · bateria/fonte", "referência do ADC · 3,0 V".
- Verificador interno agora usa a altura real do glifo (acentos, Ç, parênteses, descendentes) + folga de 0,08 mm: reproduziu os erros do KiCad e agora dá 0.
- Cobre, footprints e esquema iguais ao arquivo recebido.
