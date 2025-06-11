# Gartenbew-sserung

1. Voraussetzungen
Home Assistant (aktuelle Version)

OpenWeatherMap-Integration in Home Assistant (API-Key in secrets.yaml hinterlegt)

Telegram-Bot-Integration (Token & Chat-ID in secrets.yaml)

2. OpenWeatherMap-Sensoren einrichten
In deiner configuration.yaml oder in einem separaten Sensor-File:

yaml
Kopieren
# Beispiel für OpenWeatherMap-Sensoren
sensor:
  - platform: openweathermap
    api_key: !secret openweathermap_api_key
    monitored_conditions:
      - temperature
      - humidity
      - uv_index
      - wind_speed
      - rain
Damit tauchen unter sensor.openweathermap_* alle benötigten Werte auf.

3. Automatisierung importieren
Öffne in Home Assistant Einstellungen → Automatisierungen.

Klick auf „Importieren“ und füge die anonymisierte YAML-Datei (aus dem vorherigen Schritt) ein.

Speichere und lade die Automatisierungen neu.

4. Platzhalter anpassen
Tausche in der Automation alle sensor.YOUR_... und switch.YOUR_... durch deine tatsächlichen Entity-IDs:

sensor.YOUR_WIND_SPEED_SENSOR → z. B. sensor.openweathermap_wind_speed

switch.YOUR_WATERING_SWITCH → dein Schalter-Entity für die Pumpe

Telegram-Daten im Abschnitt notify.telegram

5. Test & Debug
Starte die Automation manuell über die UI oder simuliere einen Sonnenaufgang/-untergang.

Prüfe die Telegram-Benachrichtigungen und ob der Schalter geschaltet wird.

Logs helfen, etwaige Template-Fehler zu finden.
