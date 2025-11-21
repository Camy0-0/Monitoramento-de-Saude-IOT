# Monitoramento de Saúde com Arduino UNO R4 WiFi e MQTT

## Resumo
Projeto de monitoramento de sinais vitais (BPM, SpO2, temperatura, passos) com Arduino UNO R4 WiFi, sensores MAX30102, MLX90614 e MPU6050. Dados publicados via MQTT para broker e visualizados em dashboard.

## Conteúdo do repositório
- monitor_saude_uno_r4.ino  -> sketch Arduino
- monitor_logger.py         -> script Python para log e comando
- fritzing/                  -> arquivos .fzz e imagens do diagrama
- fotos/                     -> fotos do protótipo montado
- dados/                     -> CSV de exemplo
- README.md

## Bibliotecas Arduino
Instale via Library Manager:
- Adafruit MAX30105
- Adafruit MLX90614
- Adafruit MPU6050
- PubSubClient
- (WiFi library adequada para UNO R4 WiFi)

## Wiring (resumo)
- SDA -> A4
- SCL -> A5
- MAX30102 Vcc -> 3.3V (ou 5V conforme versão), GND
- MLX90614 Vcc -> 3.3V, GND
- MPU6050 Vcc -> 3.3V, GND
- Buzzer -> D6 (com resistor/transistor se necessário)
- LED R/G/B -> D9/D10/D11 (com resistores)

## MQTT
Tópicos:
- Publish: saude/camila/data (JSON)
- Subscribe: saude/camila/commands

Exemplo payload:
{"bpm":72,"spo2":97.2,"temp":36.5,"steps":123,"ts":1630000000}

## Vídeo
Insira link do vídeo demonstrando o funcionamento com MQTT (vídeo não listado).

## Observações
- Ajuste parâmetros de sensoriamento e calibração.
- O cálculo de SpO2 e BPM real exige implementação robusta de PPG (não apenas leituras brutas).
