# Sistema de Monitoramento de Saúde — Wokwi + ESP32 + MQTT

Projeto final (Universidade Presbiteriana Mackenzie)
Simulação completa em Wokwi com ESP32 e publicação MQTT real (broker.emqx.io).

## Estrutura
- `diagram.json` — projeto Wokwi (ESP32 + LCD + LM35 + pot + LEDs + buzzer + botão)
- `monitor_saude_esp32_mqtt.ino` — firmware Arduino (ESP32)
- `README.md` — este arquivo

## Como usar (Wokwi)
1. Abra https://wokwi.com
2. Importe `diagram.json` (Upload Project)
3. Abra o `monitor_saude_esp32_mqtt.ino` no editor Wokwi (ou copie/cole)
4. Ajuste `WIFI_SSID` e `WIFI_PASS` se desejar
5. Execute a simulação

## Conectar ao MQTT Explorer
1. Baixe e abra MQTT Explorer
2. New Connection:
   - Host: `broker.emqx.io`
   - Port: `1883`
   - Client ID: (qualquer)
3. Connect → observe o tópico `health/monitor/patient01` receber JSONs a cada 15s

## Notas
- O código está preparado para Wokwi (ESP32 ADC e 3.3V)
- Para migrar para hardware real: use ESP32 DevKit, verifique alimentação do LM35 e calibragem ADC
- Topic JSON example:
  ```json
  {"bpm":75.3,"temp":36.6,"beats":12,"state":"normal","ts":1650000000}
