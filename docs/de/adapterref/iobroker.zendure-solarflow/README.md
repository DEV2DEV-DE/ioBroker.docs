---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.zendure-solarflow/README.md
title: ioBroker.zendure-solarflow
hash: QcuyOrQ5FKmuYBqRjKELMk3WJ99VoW6xB2dgaBAKpzU=
---
![Logo](../../../en/adapterref/iobroker.zendure-solarflow/admin/zendure-solarflow.png)

![NPM-Version](https://img.shields.io/npm/v/iobroker.zendure-solarflow.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.zendure-solarflow.svg)
![Anzahl der Installationen](https://iobroker.live/badges/zendure-solarflow-installed.svg)
![Aktuelle Version im stabilen Repository](https://iobroker.live/badges/zendure-solarflow-stable.svg)
![NPM](https://nodei.co/npm/iobroker.zendure-solarflow.png?downloads=true)
![Spenden](https://img.shields.io/badge/Donate-PayPal-green.svg)

# IoBroker.zendure-solarflow
**Tests:** ![Test und Freigabe](https://github.com/nograx/ioBroker.zendure-solarflow/workflows/Test%20and%20Release/badge.svg)

## Zendure Solarflow-Adapter für ioBroker
Bei diesem Projekt handelt es sich um einen ioBroker-Adapter zum Lesen von Daten aus der Zendure Solarflow Cloud API. Es verwendet die offizielle API von Zendure.
Weitere Informationen zur API finden Sie hier: https://github.com/Zendure/developer-device-data-report

Anmerkungen:

1. Sie müssen den globalen Zendure Server verwenden!

2. Es ist möglich, das Ausgabelimit mit dem im Unterordner „productId/deviceKey/control“ erstellten Status zu steuern. Bitte alle Modi in der Zendure-App deaktivieren/deaktivieren, sonst ist es nicht möglich, das Ausgabelimit festzulegen!

   ![Fenster „Solarflow-Einstellungen“.](https://raw.github.com/nograx/ioBroker.zendure-solarflow/master/Screenshots/ZendureSolarflowSettings.png)

3. Nach der Anmeldung mit dem ioBroker-Adapter werden Sie von der offiziellen iOS- oder Android-App abgemeldet. Dies ist ein normales Verhalten. Als Workaround können Sie ein zweites Zendure-Konto mit einer anderen E-Mail-Adresse erstellen und diesem Konto Zugriff auf Ihren Solarflow HUB gewähren. Dann verwenden Sie das zweite Konto für ioBroker / den Zendure Solarflow-Adapter.

## Credits
Der Dank geht an https://github.com/reinhard-brandstaedter/solarflow, was mir beim Wissen über den MQTT-Server von Zendure sehr geholfen hat! Danke!

## Spenden
Wenn Sie den Adapter nützlich für sich finden und meine Arbeit unterstützen möchten, können Sie gerne per Paypal spenden. Danke schön! (Dies ist ein persönlicher Spendenlink für Nograx, der in keiner Verbindung zum ioBroker-Projekt steht!)<br />

## Changelog
### 1.1.4 (2024-02-28)

- Fix timeout issues

### 1.1.0 (2024-02-27)

- Switched solar input 1 und 2 to adjust the behavior like the offical app
- Added Calculations folder, remaining charge and discharge time is now available as formatted time
- Added a note in the settings that this adapter only works with the global server

### 1.0.7 (2024-01-16)

- Add control for charge and discharge limit
- Update Readme Screenshot

### 1.0.6 (2024-01-16)

- Update Readme

### 1.0.5 (2024-01-15)

- Added state for both Solarflow PV inputs

### 1.0.4 (2023-12-16)

- Added Timeout for axios

### 1.0.3 (2023-12-12)

- Password is now encrypted. NOTE: You have to re-enter the password after adapter update!

### 1.0.2 (2023-12-12)

- Adapter improvements suggested by iobroker team
- Fixed battery pack temperature (data is in kelvin, so now converting to celcius)

### 1.0.1 (2023-11-03)

- Fix translations
- Use 'extendObjectAsync' instead of 'setObjectNotExistsAsync'
- First official release version

### 0.1.0-alpha.2 (2023-10-27)

- Don't stop the adapter when no login information is provided!

### 0.1.0-alpha.1 (2023-10-27)

- Fix Typescript typos

### 0.1.0-alpha.0 (2023-10-26)

- Get battery information
- Reset states if no new data comes in (e.g. when Hub goes offline). Currently the last value still persist when Hub goes offline, so you may have 'pseudo' data in your states.

### 0.0.2 (2023-10-25)

- Initital Release, retrieving Hub data, telemetry and setting the output limit works!

### 0.0.1 (2023-10-24)

- First test

## License

MIT License

Copyright (c) 2024 Peter Frommert

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.