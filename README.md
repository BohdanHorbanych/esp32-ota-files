# esp32-ota-files

Файли для OTA-практики курсу **Embedded QA Engineer** (ESP32-S3, прошивка `station_WiFi` з фічею **Smart Lamp**).

Пристрій, підключений до Wi-Fi з інтернетом, сам завантажує звідси прошивку по HTTPS і оновлюється.

## Канали та версії

- `firmware/stable.txt` - поточна stable-версія (зараз `1.4.0`), команда `ota update`
- `firmware/beta.txt` - поточна beta-версія (зараз `1.5.0`), команда `ota update beta`
- `firmware/v1.3.0/station_WiFi.bin` - стара версія
- `firmware/v1.4.0/station_WiFi.bin` - stable
- `firmware/v1.5.0/station_WiFi.bin` - beta
- `firmware/broken/station_WiFi.bin` - навмисно "бита" прошивка для перевірки rollback (`ota broken`)

Конкретну версію можна поставити командою `ota install <ver>`, наприклад `ota install 1.3.0`.
Даунгрейд на старішу версію - `ota install <ver> force`.

Це app-образи для OTA (не merged). Через esptool їх не шиють - їх качає сам пристрій.
Стартова версія v1.3.0 (merged bin) видається окремо і шиється через esptool на `0x0`.

## Посилання, які використовує прошивка

```
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/stable.txt
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/beta.txt
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/v<версія>/station_WiFi.bin
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/firmware/broken/station_WiFi.bin
```

---

# fw7: SENTRY SWM-2 (фінальна прошивка курсу)

- `fw7/stable.txt` - `2.1.0`, `ota update`
- `fw7/beta.txt` - `2.3.0`, `ota update beta`
- `fw7/v2.1.0/sentry_fw7.bin`, `fw7/v2.3.0/sentry_fw7.bin` - app-образи для OTA
- `fw7/broken/sentry_fw7.bin` - навмисно зламана прошивка для перевірки rollback (`ota broken`)

```
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/fw7/stable.txt
https://raw.githubusercontent.com/BohdanHorbanych/esp32-ota-files/main/fw7/v<версія>/sentry_fw7.bin
```

Стартова версія 2.1.0 (merged bin) шиється через esptool, далі пристрій оновлюється сам.
