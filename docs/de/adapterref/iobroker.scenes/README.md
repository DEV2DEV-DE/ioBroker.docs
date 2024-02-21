---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.scenes/README.md
title: ioBroker-Szenenadapter
hash: ULwgcxTcnF4uHfoX+HrSuMEgoWMYDUP52Qb549uTuPU=
---
![Logo](../../../en/adapterref/iobroker.scenes/admin/scenes.png)

![Anzahl der Installationen](http://iobroker.live/badges/scenes-stable.svg)
![NPM-Version](http://img.shields.io/npm/v/iobroker.scenes.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.scenes.svg)

# IoBroker-Szenenadapter
![Test und Freigabe](https://github.com/ioBroker/ioBroker.scenes/workflows/Test%20and%20Release/badge.svg) [![Übersetzungsstatus](https://weblate.iobroker.net/widgets/adapters/-/scenes/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)

_scenes Adapter_ kann Szenen erstellen und in der ioBroker-Umgebung ausführen.

**Dieser Adapter verwendet Sentry-Bibliotheken, um Ausnahmen und Codefehler automatisch an die Entwickler zu melden.** Weitere Details und Informationen zum Deaktivieren der Fehlerberichterstattung finden Sie unter [Sentry-Plugin-Dokumentation](https://github.com/ioBroker/plugin-sentry#plugin-sentry)! Sentry Reporting wird ab js-controller 3.0 verwendet.

Dieser Adapter kann drei Arten von Szenen erstellen:

- **Szenen**
- **Gruppen**
- **virtuelle Gruppen**

## Szenen
**Szenen** werden erstellt, wenn die Einstellung „set on false“ nicht verwendet wird.
Jede Szene kann einzeln konfiguriert werden, sodass Sie **Szenen** und **Gruppen** in einer Instanz des Adapters haben können.
Die **Szene** ist lediglich eine Liste von Status-IDs und -Werten, die diese Status bei Aktivierung der Szene haben müssen. Z.B. Wir haben vor Ort `scene.allLightInBath` erstellt:

```
  scene.allLightInBath
  |- hm-rpc.0.BOTTOM_LIGHT.STATE  - true
  +- hm-rpc.0.TOP_LIGHT.STATE     - true
```

Um die Szene zu aktivieren, müssen wir `scene.allLightInBath` auf true setzen (z. B. über ein Skript oder Vis). Dann werden beide Zustände auf die gewünschten Werte gesetzt, auf `true`.
Der Wert von `scene.allLightInBath` wird auch `true` sein. Wenn wir manuell zum oberen Licht wechseln, wechselt der Wert von `scene.allLightInBath` zu `false`.
Und noch einmal zu `true`, wenn wir das Licht manuell einschalten.

Fügen wir der **Szene** den Fan hinzu:

```
  scene.allLightInBath
  |- hm-rpc.0.BOTTOM_LIGHT.STATE  - true
  |- hm-rpc.0.TOP_LIGHT.STATE     - true
  |- hm-rpc.0.FAN.STATE          - true
  |- hm-rpc.0.FAN.STATE          - false (delay 60000ms)
```

In diesem Fall wird der Ventilator durch Aktivierung der **Szene** eingeschaltet und in einer Minute wieder ausgeschaltet.
Nach dem Ausschalten des Lüfters geht der Wert von `scene.allLightInBath` auf `false` über, da nicht alle Zustände den gewünschten Werten entsprechen.
Staaten mit Verspätung werden an den Berechnungen nicht beteiligt.

Sie können die Szene mit einem „Play“-Button testen.
Darüber hinaus können Sie diese **Szene** direkt mit einer anderen Szenen-ID verknüpfen. Z.B. Wenn Sie einen Sensor an der Tür haben, können Sie diesen als Auslöser auswählen:

```
  trigger
    id:        hm-rpc.0.DOOR_SENSOR.STATE
    condition: ==
    value:     true
```

Und jedes Mal, wenn Sie die Tür im Bad öffnen, werden alle Lichter mit Ventilator eingeschaltet.

## Gruppen
**Gruppen** sind wie virtuelle Kanäle. Mithilfe von **Gruppen** können Sie aus mehreren Aktoren virtuelle Geräte erstellen und diese gemeinsam wie ein Gerät steuern.
Lassen Sie uns unser Beispiel mit den Lichtern des Bades modifizieren.

```
  scene.allLightInBath             "set on true"    "set on false"
  |- hm-rpc.0.BOTTOM_LIGHT.STATE  - true             false
  +- hm-rpc.0.TOP_LIGHT.STATE     - true             false
```

Wenn Sie diese **Gruppe** mit dem Türsensor verknüpfen, wie folgt:

```
  trigger on true
    id:        hm-rpc.0.DOOR_SENSOR.STATE
    condition: ==
    value:     true

  trigger on false
    id:        hm-rpc.0.DOOR_SENSOR.STATE
    condition: ==
    value:     false
```

Jedes Mal, wenn Sie die Tür öffnen, werden alle Lichter in einer Badewanne eingeschaltet. Der Wert von `scene.allLightInBath` wird auf **true** gesetzt.
Wenn Sie die Tür schließen, wird das Licht ausgeschaltet und der Wert von `scene.allLightInBath` geht auf **false**.

Es ist nutzlos, aber als Beispiel gut.

Wenn Sie ein Licht manuell einschalten, geht der Wert von `scene.allLightInBath` auf **unsicher**.

Verzögerungen können auch in der **Gruppe** verwendet werden, aber die Zustände mit Verzögerung werden nicht an der Berechnung des aktuellen Werts der **Gruppe** beteiligt.

## Virtuelle Gruppen
**Virtuelle Gruppen** sind wie virtuelle Kanäle und Gruppen, können aber beliebige Werte haben: Zahlen, Zeichenfolgen usw.
Sie können eine virtuelle Gruppe erstellen, um alle Rollläden im Wohnzimmer zu steuern.
Durch das Schreiben von 40 % in eine virtuelle Gruppe werden alle Rollläden auf 40 % gesetzt.

Darüber hinaus können Sie das Verhalten definieren, bei dem der Wert für die Gruppe übernommen werden soll, wenn nicht alle Zustände der Gruppe den gleichen Wert haben.

Sie können folgende Aggregationen bereitstellen (nur im erweiterten Modus verfügbar):

- „unsicher“ – (Standard) – der Wert der Gruppe hat den Text „unsicher“.
- „any“ – erster Nicht-Null-Wert aller Zustände in einer Gruppe.
- „min“ – Minimalwert aller Zustände in einer Gruppe.
- „max“ – Maximalwert aller Zustände in einer Gruppe.
- „avg“ – Durchschnittswert aller Zustände in einer Gruppe.

## Aktuelle Zustände als Szene speichern
Um aktuelle Zustände in einer Szene zu speichern, können Sie eine Nachricht an den Adapter senden:

```
sendTo(
    'scenes.0',
    'save',
    {sceneId:
        'scene.0.SCENE_ID', // scene ID
        isForTrue: true     // true if actual values must be saved for `true` state and `false` if for false
    },
    result => result.err && console.error(result.error) // optional
);
```

Der Adapter liest alle tatsächlichen Werte für die in dieser Szene definierten IDs und speichert sie als konfigurierte Werte.

## Szene per Nachricht deaktivieren oder aktivieren Um eine Szene zu deaktivieren oder zu aktivieren, können Sie eine Nachricht an den Adapter senden:
```
// enable
sendTo(
    'scenes.0',
    'enable',
    'scene.0.SCENE_ID',
    result => result.err && console.error(result.error) // optional
);
// disable
sendTo(
    'scenes.0',
    'disable',
    'scene.0.SCENE_ID',
    result => result.err && console.error(result.error) // optional
);
// or
sendTo(
    'scenes.0',
    'disable', // 'enable' to enable
    {sceneId: 'scene.0.SCENE_ID'},
    result => result.err && console.error(result.error) // optional
);
```

<!-- Platzhalter für die nächste Version (am Anfang der Zeile):

### **ARBEIT IN ARBEIT** -->

## Changelog
### 3.0.1 (2024-02-16)
* (bluefox) Cleared cron tasks by re-init
* (bluefox) CRON Editor dialog added
* (bluefox) Implemented scene enabling/disabling via messages
* (bluefox) Implemented the writing of the scene states with ack=true
* (bluefox) Added description to the scene states
* (bluefox) Added possibility to use categories/enumerations

### 2.4.2 (2024-02-12)
* (bluefox) Preserved empty folders by renaming and moving of scenes

### 2.4.0 (2022-12-23)
* (Apollon77) prevent a crash case reported by Sentry
* (bluefox) Updated some GUI libraries

### 2.3.9 (2022-02-13)
* (bluefox) Updated some GUI libraries
* (bluefox) Updated releaser

### 2.3.8 (2021-08-31)
* (Apollon77) Handles a case where states are not set but used as value (Sentry IOBROKER-SCENES-13)
* (TyrionWarMage) Added the aggregation mode for the virtual groups.
* (bluefox) Sentry data will not be sent in front-end if the diagnostic or sentry is disabled

### 2.3.6 (2021-01-22)
* (Apollon77) Check state id before getting value (Sentry IOBROKER-SCENES-F)

### 2.3.5 (2021-01-22)
* (Apollon77) Add error logging if invalid ids are configured for scenes (Sentry IOBROKER-SCENES-Y)

### 2.3.4 (2021-01-16)
* (Apollon77) Prevent a crash case (Sentry IOBROKER-SCENES-X, IOBROKER-SCENES-V)

### 2.3.3 (2020-12-06)
* (bluefox) Implemented drag&drop for the reorder of scenes in folders
* (bluefox) Implemented Easy mode
* (bluefox) Possibility to use set point from another state

### 2.3.1 (2020-11-06)
* (Apollon77) Prevent a crash case (Sentry IOBROKER-SCENES-M)

### 2.3.0 (2020-11-02)
* (bluefox) Fixed GUI errors

### 2.1.7 (2020-10-30)
* (Apollon77) Prevent a crash case (Sentry IOBROKER-SCENES-E, IOBROKER-SCENES-G, IOBROKER-SCENES-A)

### 2.1.6 (2020-09-25)
* (bluefox) Updated the select ID dialog.

### 2.1.3 (2020-09-18)
* (Apollon77) Prevent crash cases (Sentry IOBROKER-SCENES-B, IOBROKER-SCENES-8, IOBROKER-SCENES-D)

### 2.1.2 (2020-07-08)
* (bluefox) Interval between states was corrected

### 2.0.17 (2020-06-29)
* (bluefox) GUI error corrected

### 2.0.13 (2020-06-27)
* (bluefox) Mobile view added

### 2.0.12 (2020-06-26)
* (bluefox) GUI error corrected

### 2.0.10 (2020-06-20)
* (bluefox) Added "Do not overwrite state if it has the required value" option

### 2.0.9 (2020-06-17)
* (bluefox) The colors are corrected

### 2.0.8 (2020-06-16)
* (bluefox) The tolerance is implemented

### 2.0.3 (2020-06-14)
* (bluefox) New GUI based on React

### 1.1.1 (2019-05-26)
* (bluefox) Added storing of actual values in a scene via a message

### 1.1.0 (2018-04-24)
* (bluefox) Works now with Admin3

### 1.0.2 (2018-01-21)
* (bluefox) use new select ID dialog
* (DeepCoreSystem) translations
* (paul53) text fixes

### 1.0.0 (2017-11-11)
* (bluefox) fix false scenes

### 0.2.7 (2017-08-14)
* (bluefox) Support of iobroker.pro

### 0.2.6 (2016-06-21)
* (bluefox) add read/write settings to scene object

### 0.2.5 (2016-02-03)
* (bluefox) update node-schedule

### 0.2.4 (2016-01-24)
* (bluefox) fix error disabled states in a scene

### 0.2.3 (2015-12-10)
* (bluefox) fix error with trigger on false

### 0.2.2 (2015-11-22)
* (bluefox) fix error with restart adapter

### 0.2.1 (2015-10-27)
* (bluefox) delete triggers if virtual groups enabled

### 0.2.0 (2015-10-27)
* (bluefox) support of virtual groups

### 0.1.3 (2015-09-19)
* (bluefox) show set value if 0 or false in settings

### 0.1.2 (2015-08-15)
* (bluefox) add translations
* (bluefox) try to fix error by renaming

### 0.1.1 (2015-08-10)
* (bluefox) allow description for states in a scene
* (bluefox) check by rename if the scene with the same name yet exists
* (bluefox) allowed a coping of a scene
* (bluefox) fix error with delay and stopAllDelays settings

### 0.1.0 (2015-08-09)
* (bluefox) fix error with delays and config change
* (bluefox) implement replace

### 0.0.2 (2015-08-05)
* (bluefox) change configuration schema
* (bluefox) add cron
* (bluefox) add a burst interval

### 0.0.1 (2015-07-29)
* (bluefox) initial commit

## License
The MIT License (MIT)

Copyright (c) 2015-2024, Bluefox (dogafox@gmail.com)

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