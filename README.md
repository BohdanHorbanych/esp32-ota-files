# esp32-ota-files

Файли для OTA-демо курсу **Embedded QA Engineer** (ESP32-S3, прошивка `station_WiFi`).

Пристрій, підключений до Wi-Fi з інтернетом, сам завантажує звідси прошивку по HTTPS і оновлюється.

## Файли

| Файл | Що це |
|---|---|
| `firmware/station_WiFi.bin` | робоча прошивка **v1.4.0** - на неї оновлюється пристрій командою `ota update` |
| `firmware/station_WiFi_broken.bin` | навмисно "бита" прошивка **v1.5.0-broken** - для демо rollback (`ota broken`) |
| `firmware/version.txt` | остання доступна версія (читає команда `ota check`) |

Це app-образи для OTA (не merged). Через esptool їх не шиють - їх качає сам пристрій.

## Сценарій

1. Прошити стартову версію **v1.3.0** (merged bin, видається окремо) через esptool на `0x0`.
2. `connect` - підключитися до Wi-Fi (2.4 GHz, з інтернетом).
3. `version` - `FW: v1.3.0`, partition `ota_0`.
4. `ota check` - `current 1.3.0`, `available 1.4.0`.
5. `ota update` - прогрес 0-100%, reboot, у boot log `self-check passed, firmware marked VALID`, `version` - `v1.4.0`, partition `ota_1`.
6. `ota broken` - завантажується v1.5.0-broken, після reboot self-check падає, пристрій сам повертається на попередню версію (rollback).

## Посилання, які використовує прошивка

```
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/station_WiFi.bin
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/station_WiFi_broken.bin
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/version.txt
```
