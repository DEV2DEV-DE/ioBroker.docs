---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.kecontact/README.md
title: ioBroker.kecontact
hash: 9/sySE0ECgXNW2H1f5TUXan07P4AqiT2aJWxktjYLo0=
---
![Logo](../../../en/adapterref/iobroker.kecontact/admin/kecontact.png)

![NPM-Version](https://img.shields.io/npm/v/iobroker.kecontact.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.kecontact.svg)
![Anzahl der Installationen (aktuell)](https://iobroker.live/badges/kecontact-installed.svg)
![Anzahl Installationen (stabil)](https://iobroker.live/badges/kecontact-stable.svg)
![Abhängigkeitsstatus](https://img.shields.io/david/iobroker-community-adapters/iobroker.kecontact.svg)
![NPM](https://nodei.co/npm/iobroker.kecontact.png?downloads=true)

# IoBroker.kecontact
[![Übersetzungsstatus](https://weblate.iobroker.net/widgets/adapters/-/kecontact/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)

**Tests:** ![Test und Freigabe](https://github.com/iobroker-community-adapters/ioBroker.kecontact/workflows/Test%20and%20Release/badge.svg)

# IoBroker-Adapter für KEBA KeContact P20 oder P30 und BMW i Wallbox
Steuern Sie Ihre Ladestation über das UDP-Protokoll und nutzen Sie die automatische Regelung z.B. zum Laden Ihres Fahrzeugs durch Photovoltaik-Überschuss und Batteriespeicher.

## Installieren
Installieren Sie diesen Adapter über ioBroker Admin:

1. Öffnen Sie den Instanzkonfigurationsdialog
2. Geben Sie die IP-Adresse Ihrer KEBA KeContact Wallbox ein
3. Geben Sie die Zustände der Energiezähler für die PV-Automatik oder Leistungsbegrenzung sowie die gewünschten Daten für die Batteriespeicherung ein
4. Speichern Sie die Konfiguration
5. Starten Sie den Adapter

## Aufbau
### KeContact IP-Adresse
Dies ist die IP-Adresse Ihrer KEBA KeContact oder BMW i Wallbox. Kombination mit Keba KeContact S10 (Phasenumschaltgerät) wird unterstützt.

### Firmware-Überprüfung
Wird nicht mehr unterstützt, da die Website von Keba geändert wurde.

### Passivmodus
Aktivieren Sie diese Option, wenn Sie Ihre Wallbox selbst steuern möchten und nicht möchten, dass dieser Adapter einige Automatikfunktionen ausführt. In diesem Fall werden alle weiteren Optionen bezüglich PV-Automatik und Leistungsbegrenzung ignoriert.

### Nachträgliche Wallbox
Aktivieren Sie diese Option, wenn es sich um eine nachfolgende Wallbox in Ihrer Umgebung handelt. Derzeit kann nur eine Wallbox aktiv verwaltet werden. Alle anderen (separaten Instanzen) müssen diese Option aktivieren, da nur eine Instanz Broadcast-Nachrichten empfangen kann. Diese Wallbox/Instanz wird im passiven Modus betrieben.

### Ladesitzungen laden
Sie können diese Option aktivieren, um regelmäßig die neuesten Ladevorgänge (30) von Ihrer Wallbox herunterzuladen.
ACHTUNG für Benutzer ab Version v1.1.1 und niedriger: Sie müssen diese Option aktivieren, um weiterhin Ladevorgänge zu erhalten!

### Aktualisierungsintervall
Dies ist das Intervall in Sekunden, wie oft die Wallbox nach neuen Ladewerten abgefragt werden soll.

Der Standardwert beträgt 10 Minuten, was ein gutes Gleichgewicht zwischen der Auslastung von KeConnect und der Verfügbarkeit aktueller Informationen in ioBroker darstellt.

### PV-Automatik
Um Ihr Fahrzeug entsprechend einem Überschuss zu laden (z. B. durch Photovoltaik), können Sie auch Zustände definieren, die Überschuss und Berücksichtigung der Hauptstromversorgung darstellen. Diese Werte werden zur Berechnung der Stromstärke verwendet, die zum Laden verwendet werden kann. Durch zusätzliche Werte können Sie definieren

* ein Zustand zum Umschalten der Ladephasen 1p/3p oder über den X2-Anschluss von Keba Kecontact (mit Keba KeContact S10 oder einem anderen Schütz)
* ein Status für die aktuelle Leistung des Batteriespeichers, sodass die Photovoltaik-Automatik diese zusätzlich zum Laden Ihres Fahrzeugs nutzt
* eine Option zur Begrenzung der Leistung des Batteriespeichers, um den Ladevorgang nur mit minimaler Leistung aufrechtzuerhalten
* Schalten Sie die X1-Option um, wenn Sie den X1-Eingang der Ladestation verwenden möchten, um zu steuern, ob mit voller Leistung oder per Photovoltaik-Automatik geladen werden soll
* eine andere Mindeststromstärke als die standardmäßigen 6 A (nur erforderlich für z. B. Renault Zoe)
* ein Wert für die Leistung, die zum Starten des Ladevorgangs verwendet werden kann (d. h. der Ladevorgang beginnt auch dann, wenn nicht genügend Überschuss verfügbar ist – empfohlen 0 W für 1-Phasen-Ladevorgang, 500 W bis 2000 W für 3-Phasen-Ladevorgang)
* ein Inkrement für die Stromstärke (empfohlen 500 mA)
* ein Wert der Rücksichtnahme, der vorübergehend zum Aufrechterhalten der Ladesitzung verwendet werden kann (das bedeutet, dass der Ladevorgang später gestoppt wird, auch wenn nicht mehr genügend Überschuss verfügbar ist – Startrücksicht wird hinzugefügt – empfohlen 500 W)
* Mindestdauer des Ladevorgangs (auch wenn der Überschuss nicht mehr ausreicht, dauert ein Ladevorgang mindestens diese Zeit – empfohlen 300 Sekunden)
* Zeit zum Fortsetzen des Ladevorgangs jedes Mal, wenn der Überschuss nicht mehr ausreicht (zur Überbrückung der Zeit an bewölkten Tagen)

### 1p/3p Aufladung
Wenn Sie über ein Installationsschütz zum (Trennen) der Phasen 2 und 3 Ihrer Ladestation verfügen und dieser Schalter durch einen Zustand ausgelöst werden kann, ist dieser Adapter in der Lage, den Ladevorgang mit einer Phase zu starten und auf den 3-Phasen-Ladevorgang umzuschalten, wenn Ihr Überschuss ausreicht dafür.
Geben Sie in diesem Fall bitte den Zustand Ihres Installationsschützes ein und ob es sich um NO (normally open) oder NC (normally close) handelt.

### Batteriespeicher
Wenn Sie einen Batteriespeicher besitzen, füllen Sie bitte hier die Optionen aus. Durch die Angabe von Zuständen für Überschuss und Berücksichtigung Ihres Batteriespeichers kann dieser Adapter abhängig von der in den Optionen festgelegten Strategie steuern, ob Batteriespeicher zum Laden Ihres Fahrzeugs verwendet werden soll oder nicht.

### Leistungsbegrenzung
Sie können auch max. begrenzen. Leistung Ihrer Wallbox, um den Hauptstrom zu begrenzen. Z.B. Beim Betrieb von Nachtspeicherheizungen müssen Sie ggf. eine maximale Leistungsbegrenzung beachten.
Wenn Sie einen Wert eingeben, wird Ihre Wallbox kontinuierlich begrenzt, um Ihr Leistungslimit nicht zu überschreiten.
Zur Begrenzung können bis zu drei Zustände von Energiezählern vorgegeben werden. Zur Berechnung des aktuellen Verbrauchs werden alle Werte addiert.
Über ein zusätzliches Kontrollkästchen wird festgelegt, ob die Wallbox-Leistung einbezogen wird (in diesem Fall wird die Wallbox-Leistung von den Statuswerten abgezogen).

### Dynamische Optionen
Darüber hinaus gibt es einige Zustände, die das Verhalten der Photovoltaik-Automatik im laufenden Betrieb beeinflussen können, z.B. durch ein eigenes Skript, das diese Werte entsprechend Ihren Anforderungen aktualisiert)

* kecontact.n.automatic.photovoltaics – Aktiviert die Photovoltaik-Automatik (true) oder lädt das Fahrzeug mit maximaler Leistung, wenn es auf false gesetzt ist
* kecontact.n.automatic.calcPhases – definiert die aktuelle Anzahl der Phasen, die für die Ladeberechnung verwendet werden sollen. Dieser wird für die Keba Deutschland Edition benötigt und kann für die Erstladung aller Ladestationen genutzt werden
* kecontact.n.automatic.addPower – definiert die Menge an Watt, die zum Laden Ihres Fahrzeugs zulässig ist (wie in den Optionen).
* kecontact.n.automatic.pauseWallbox – stoppt jeden Ladevorgang sofort, solange dieser auf „true“ gesetzt ist
* kecontact.n.automatic.limitCurrent – begrenzt Ihren Ladevorgang auf die angegebene Stromstärke in mA (0 = keine Begrenzung)
* kecontact.n.automatic.batteryStorageStrategy – Strategie, ob und wie Ihr Batteriespeicher zum Laden Ihres Fahrzeugs genutzt werden soll
* kecontact.n.automatic.batterySoCForCharging – Beschränken Sie die Nutzung des Batteriespeichers für das Fahrzeug, indem Sie einen SoC angeben, unterhalb dessen das Laden verboten ist

Beispiel: Um Ihr Fahrzeug unabhängig vom Überschuss mit einer konstanten Stromstärke von 6 A zu laden, stellen Sie „Photovoltaik“ auf „false“ und limitCurrent auf 6000.

## Legal
Dieses Projekt steht in keiner direkten oder indirekten Verbindung zur Firma KEBA AG.

KeConnect ist eine eingetragene Marke der KEBA AG.

## Changelog

<!--
  Placeholder for the next version (at the beginning of the line):
  ### **WORK IN PROGRESS**
-->
### 2.1.0 (2024-01-06)
* (Sneak-L8) multiple options for battery storage strategy
* (Sneak-L8) added names for values of some states: state, plug, timeQ and batteryStorageStrategy
* (Sneak-L8) don't try to charge when state is 5 (auth req, car not ready, ...)
* (Sneak-L8) new state to dynamically set SoC above which battery storage may be used for charging vehicle

### 2.0.2 (2023-10-10)
* (Sneak-L8) default value for minimum regard time (180 seconds)
* (Sneak-L8) fix calculation of phases for reduced charging
* (chrisko) added minimum timer to switch between phases if 1p/3p charging is used.
* (Sneak-L8) disable firmware check for c-series due to changes on webpage of Keba
* (Sneak-L8) sometimes 1p/3p switch was not working correctly (repeatedly "stop charging fpr switch of phases...")

### 2.0.1 (2023-07-10)
* (Sneak-L8) support for Company Car Wall Box MID - GREEN EDITION (sentry IOBROKER-KECONTACT-1K & IOBROKER-KECONTACT-1N) and PV-Edition (sentry IOBROKER-KECONTACT-1M)

### 2.0.0 (2023-06-26)
* (Sneak-L8) support for 1p/3p-charging (start charging with 1 phase and switch to 3 phases when enough surplus available) including Keba KeContact S10
* (Sneak-L8) minimum amperage allowed to 5A because some vehicles and KeContact (undocumented) allow this value
* (Sneak-L8) new switch to limit battery storage support only to hold minimum charging power
* (Sneak-L8) catch error when requesting firmware page (sentry IOBROKER-KECONTACT-1H)
* (Sneak-L8) RFID tag and class where not updated in channel "statitics" when no charging sessions were obtained
* (Sneak-L8) added new Keba model Company Car Wall Box MID (sentry IOBROKER-KECONTACT-1K)

### 1.5.2 (2022-11-02)
* (Sneak-L8) fix error in release script

## License
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      copyright notice that is included in or attached to the work
      (an example is provided in the Appendix below).

      "Derivative Works" shall mean any work, whether in Source or Object
      form, that is based on (or derived from) the Work and for which the
      editorial revisions, annotations, elaborations, or other modifications
      represent, as a whole, an original work of authorship. For the purposes
      of this License, Derivative Works shall not include works that remain
      separable from, or merely link (or bind by name) to the interfaces of,
      the Work and Derivative Works thereof.

      "Contribution" shall mean any work of authorship, including
      the original version of the Work and any modifications or additions
      to that Work or Derivative Works thereof, that is intentionally
      submitted to Licensor for inclusion in the Work by the copyright owner
      or by an individual or Legal Entity authorized to submit on behalf of
      the copyright owner. For the purposes of this definition, "submitted"
      means any form of electronic, verbal, or written communication sent
      to the Licensor or its representatives, including but not limited to
      communication on electronic mailing lists, source code control systems,
      and issue tracking systems that are managed by, or on behalf of, the
      Licensor for the purpose of discussing and improving the Work, but
      excluding communication that is conspicuously marked or otherwise
      designated in writing by the copyright owner as "Not a Contribution."

      "Contributor" shall mean Licensor and any individual or Legal Entity
      on behalf of whom a Contribution has been received by Licensor and
      subsequently incorporated within the Work.

   2. Grant of Copyright License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      copyright license to reproduce, prepare Derivative Works of,
      publicly display, publicly perform, sublicense, and distribute the
      Work and such Derivative Works in Source or Object form.

   3. Grant of Patent License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      (except as stated in this section) patent license to make, have made,
      use, offer to sell, sell, import, and otherwise transfer the Work,
      where such license applies only to those patent claims licensable
      by such Contributor that are necessarily infringed by their
      Contribution(s) alone or by combination of their Contribution(s)
      with the Work to which such Contribution(s) was submitted. If You
      institute patent litigation against any entity (including a
      cross-claim or counterclaim in a lawsuit) alleging that the Work
      or a Contribution incorporated within the Work constitutes direct
      or contributory patent infringement, then any patent licenses
      granted to You under this License for that Work shall terminate
      as of the date such litigation is filed.

   4. Redistribution. You may reproduce and distribute copies of the
      Work or Derivative Works thereof in any medium, with or without
      modifications, and in Source or Object form, provided that You
      meet the following conditions:

      (a) You must give any other recipients of the Work or
          Derivative Works a copy of this License; and

      (b) You must cause any modified files to carry prominent notices
          stating that You changed the files; and

      (c) You must retain, in the Source form of any Derivative Works
          that You distribute, all copyright, patent, trademark, and
          attribution notices from the Source form of the Work,
          excluding those notices that do not pertain to any part of
          the Derivative Works; and

      (d) If the Work includes a "NOTICE" text file as part of its
          distribution, then any Derivative Works that You distribute must
          include a readable copy of the attribution notices contained
          within such NOTICE file, excluding those notices that do not
          pertain to any part of the Derivative Works, in at least one
          of the following places: within a NOTICE text file distributed
          as part of the Derivative Works; within the Source form or
          documentation, if provided along with the Derivative Works; or,
          within a display generated by the Derivative Works, if and
          wherever such third-party notices normally appear. The contents
          of the NOTICE file are for informational purposes only and
          do not modify the License. You may add Your own attribution
          notices within Derivative Works that You distribute, alongside
          or as an addendum to the NOTICE text from the Work, provided
          that such additional attribution notices cannot be construed
          as modifying the License.

      You may add Your own copyright statement to Your modifications and
      may provide additional or different license terms and conditions
      for use, reproduction, or distribution of Your modifications, or
      for any such Derivative Works as a whole, provided Your use,
      reproduction, and distribution of the Work otherwise complies with
      the conditions stated in this License.

   5. Submission of Contributions. Unless You explicitly state otherwise,
      any Contribution intentionally submitted for inclusion in the Work
      by You to the Licensor shall be under the terms and conditions of
      this License, without any additional terms or conditions.
      Notwithstanding the above, nothing herein shall supersede or modify
      the terms of any separate license agreement you may have executed
      with Licensor regarding such Contributions.

   6. Trademarks. This License does not grant permission to use the trade
      names, trademarks, service marks, or product names of the Licensor,
      except as required for reasonable and customary use in describing the
      origin of the Work and reproducing the content of the NOTICE file.

   7. Disclaimer of Warranty. Unless required by applicable law or
      agreed to in writing, Licensor provides the Work (and each
      Contributor provides its Contributions) on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
      implied, including, without limitation, any warranties or conditions
      of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
      PARTICULAR PURPOSE. You are solely responsible for determining the
      appropriateness of using or redistributing the Work and assume any
      risks associated with Your exercise of permissions under this License.

   8. Limitation of Liability. In no event and under no legal theory,
      whether in tort (including negligence), contract, or otherwise,
      unless required by applicable law (such as deliberate and grossly
      negligent acts) or agreed to in writing, shall any Contributor be
      liable to You for damages, including any direct, indirect, special,
      incidental, or consequential damages of any character arising as a
      result of this License or out of the use or inability to use the
      Work (including but not limited to damages for loss of goodwill,
      work stoppage, computer failure or malfunction, or any and all
      other commercial damages or losses), even if such Contributor
      has been advised of the possibility of such damages.

   9. Accepting Warranty or Additional Liability. While redistributing
      the Work or Derivative Works thereof, You may choose to offer,
      and charge a fee for, acceptance of support, warranty, indemnity,
      or other liability obligations and/or rights consistent with this
      License. However, in accepting such obligations, You may act only
      on Your own behalf and on Your sole responsibility, not on behalf
      of any other Contributor, and only if You agree to indemnify,
      defend, and hold each Contributor harmless for any liability
      incurred by, or claims asserted against, such Contributor by reason
      of your accepting any such warranty or additional liability.

   END OF TERMS AND CONDITIONS

   APPENDIX: How to apply the Apache License to your work.

      To apply the Apache License to your work, attach the following
      boilerplate notice, with the fields enclosed by brackets "[]"
      replaced with your own identifying information. (Don't include
      the brackets!)  The text should be enclosed in the appropriate
      comment syntax for the file format. We also recommend that a
      file or class name and description of purpose be included on the
      same "printed page" as the copyright notice for easier
      identification within third-party archives.

   Copyright 2021-2024 UncleSamSwiss, Sneak-L8

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.