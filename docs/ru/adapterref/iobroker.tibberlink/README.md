---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.tibberlink/README.md
title: ioBroker.tibberlink
hash: 7fN5FrABztCO5Y6BdXIVUph4eWcQ6o7gvfNwt8kBJC4=
---
![Логотип](../../../en/adapterref/iobroker.tibberlink/admin/tibberlink.png)

![НПМ-версия](https://img.shields.io/npm/v/iobroker.tibberlink?style=flat-square)
![Загрузки](https://img.shields.io/npm/dm/iobroker.tibberlink?label=npm%20downloads&style=flat-square)
![узел-lts](https://img.shields.io/node/v-lts/iobroker.tibberlink?style=flat-square)
![Статус зависимости Libraries.io для последней версии](https://img.shields.io/librariesio/release/npm/iobroker.tibberlink?label=npm%20dependencies&style=flat-square)
![GitHub](https://img.shields.io/github/license/hombach/iobroker.tibberlink?style=flat-square)
![Размер репозитория GitHub](https://img.shields.io/github/repo-size/hombach/iobroker.tibberlink?logo=github&style=flat-square)
![Действия по фиксации GitHub](https://img.shields.io/github/commit-activity/m/hombach/iobroker.tibberlink?logo=github&style=flat-square)
![Последний коммит GitHub](https://img.shields.io/github/last-commit/hombach/iobroker.tibberlink?logo=github&style=flat-square)
![Проблемы с GitHub](https://img.shields.io/github/issues/hombach/iobroker.tibberlink?logo=github&style=flat-square)
![Статус рабочего процесса GitHub](https://img.shields.io/github/actions/workflow/status/hombach/iobroker.tibberlink/test-and-release.yml?branch=main&logo=github&style=flat-square)
![Аппвейор-CI](https://ci.appveyor.com/api/projects/status/github/hombach/ioBroker.tibberlink?branch=master&svg=true)
![Известные уязвимости SNYK](https://snyk.io/test/github/hombach/ioBroker.tibberlink/badge.svg)
![Бета](https://img.shields.io/npm/v/iobroker.tibberlink.svg?color=red&label=beta)
![Стабильный](https://iobroker.live/badges/tibberlink-stable.svg)
![Установлен](https://iobroker.live/badges/tibberlink-installed.svg)
![НПМ](https://nodei.co/npm/iobroker.tibberlink.png?downloads=true)

# IoBroker.tibberlink
[![CodeQL] (https://github.com/hombach/ioBroker.tibberlink/actions/workflows/codeql-anasis.yml/badge.svg)](https://github.com/hombach/ioBroker.tibberlink/actions/workflows/codeql-analysis.yml)

## Версии
## Адаптер для использования данных об энергии TIBBER в ioBroker
Этот адаптер облегчает подключение данных из API вашей учетной записи Tibber для использования в ioBroker, будь то для одного дома или нескольких домов.

Если вы в настоящее время не являетесь пользователем Tibber, я был бы очень признателен, если бы вы использовали мою реферальную ссылку: [Реферальная ссылка Тиббера](https://invite.tibber.com/mu8c82n5).

## Стандартная конфигурация
- Начните с создания нового экземпляра адаптера.
- Вам также потребуется токен API от Tibber, который вы можете получить здесь: [Tibber Developer API](https://developer.tibber.com).
- Введите свой токен API Tibber в стандартных настройках и настройте хотя бы одну строку для настроек прямой трансляции (выберите «Нет доступно»).
- Сохраните настройки и выйдите из конфигурации, чтобы перезагрузить адаптер; этот шаг позволяет в первый раз запросить ваш дом(ы) с сервера Tibber.
- Вернитесь на экран конфигурации и выберите дома, из которых вы хотите получать данные в реальном времени с помощью Tibber Pulse. Вы также можете выбрать дома и отключить ленту (Примечание: это работает, только если оборудование установлено и сервер Tibber проверил соединение с Pulse).
- У вас есть возможность отключить получение данных о ценах на сегодня и завтра, например, если вы собираетесь использовать только прямые трансляции Pulse.
- При желании вы можете включить получение исторических данных о потреблении. Укажите количество наборов данных для часов, дней, недель, месяцев и лет. Вы можете использовать «0», чтобы отключить один или несколько из этих интервалов в зависимости от ваших предпочтений.
- Примечание. Очень важно помнить о размере набора данных, поскольку слишком большие запросы могут привести к отсутствию ответа от сервера Tibber. Мы рекомендуем поэкспериментировать с размером набора данных, чтобы обеспечить оптимальную функциональность. Настройка интервалов и количества наборов данных может помочь найти правильный баланс между получением ценных данных и поддержанием скорости реагирования сервера. Например. 48 — вполне хорошая сумма для часов.
- Сохраните настройки.

## Конфигурация калькулятора
- Теперь, когда соединение Tibber установлено и работает, вы также можете использовать калькулятор для включения дополнительных функций автоматизации в адаптер TibberLink.
- Калькулятор работает с использованием каналов, каждый из которых связан с выбранным домом.
- Эти каналы можно активировать или деактивировать в зависимости от соответствующих состояний.
— Эти состояния предназначены для использования в качестве внешних динамических входных данных для TibberLink, что позволяет вам, например, корректировать предельную стоимость («TriggerPrice») из внешнего источника или отключать канал калькулятора («Активный»).
- Состояния канала калькулятора располагаются рядом с исходными состояниями и называются в соответствии с номером канала. При этом здесь отображается имя канала, выбранное на экране администратора, чтобы лучше идентифицировать ваши конфигурации.

    ![Состояния калькулятора](../../../en/adapterref/iobroker.tibberlink/docu/calculatorStates.png)

- Поведение каждого канала определяется его типом: «лучшая стоимость (LTF)», «лучшие отдельные часы (LTF)», «лучший блок часов (LTF)» или «умный буфер батареи».
- Каждый канал заполняет одно или два внешних состояния в качестве выхода, которые необходимо выбрать на вкладке настроек. Например, это состояние может быть «0_userdata.0.example_state» или любым другим доступным для записи внешним состоянием.
- Значения, которые должны быть записаны в выходное состояние, могут быть определены в «значении ДА» и «значении НЕТ», например, «истина» для логических состояний или числа или текста для записи.
- Выходы:
    - «Лучшая стоимость»: использует состояние «TriggerPrice» в качестве входных данных, выдавая выходной сигнал «ДА» каждый час, когда текущая стоимость энергии Tibber ниже триггерной цены.
    - «Лучшие отдельные часы»: генерирует вывод «ДА» в течение самых дешевых часов, число которых определяется в состоянии «AmountHours».
    - «Блок лучших часов»: выводит «ДА» в течение наиболее экономически эффективного блока часов с количеством часов, указанным в состоянии «AmountHours».

        Кроме того, средняя общая стоимость в определенном блоке записывается в состояние «AverageTotalCost» рядом с входными состояниями этого канала. Также в результате расчета в «BlockStartFullHour» и «BlockEndFullHour» записывается начальный и конечный час блока.

    - «Лучшая стоимость LTF»: «Лучшая стоимость» в течение ограниченного периода времени (LTF).
    - «Лучшие отдельные часы LTF»: «Лучшие отдельные часы» в течение ограниченного периода времени (LTF).
    - «Блок лучших часов LTF»: «Блок лучших часов» в течение ограниченного периода времени (LTF).
    - «Smart Battery Buffer»: используйте параметр «EfficiencyLoss», чтобы указать потерю эффективности аккумуляторной системы. Параметр «EfficiencyLoss» может принимать значения от 0 до 1, где 0 означает отсутствие потери эффективности, а 1 — полную потерю эффективности. Например, значение 0,25 указывает на потерю эффективности на 25 % за цикл зарядки/разрядки.

        Используйте параметр «AmountHours», чтобы ввести желаемое количество часов для зарядки аккумулятора. Калькулятор активирует зарядку батареи («значение ДА») и отключит питание батареи («значение 2 НЕТ») в течение указанных «AmountHours» самых дешевых часов. И наоборот, он отключит зарядку батареи («значение НЕТ») и активирует питание батареи («значение 2 ДА») в часы с самой высокой стоимостью, при условии, что стоимость выше, чем самая высокая общая цена среди дешевых часов. В остальные обычные часы, когда буферизация энергии с помощью аккумулятора экономически нецелесообразна, оба выхода будут отключены.

- Каналы LTF: функционируют аналогично стандартным каналам, но работают только в пределах временного интервала, определенного объектами состояния «StartTime» и «StopTime». После «StopTime» канал деактивируется. «StartTime» и «StopTime» могут охватывать несколько дней. Состояния должны быть заполнены строкой даты и времени в формате ISO-8601 со смещением часового пояса, например: «2024-01-17T21:00:00.000+01:00». Кроме того, у каналов появился новый параметр состояния под названием «RepeatDays», для которого по умолчанию установлено значение 0. Если для параметра «RepeatDays» установлено положительное целое значение, канал будет повторять свой цикл, увеличивая StartTime и StopTime на количество дней, указанное в «RepeatDays», как только будет достигнуто значение StopTime. Например. Для ежедневного повторения установите для параметра «RepeatDays» значение 1».

### Подсказки
#### Обратное использование
Чтобы получить, например, часы пик вместо оптимальных часов, просто поменяйте местами использование и параметры: ![Состояния калькулятора обратные](../../../en/adapterref/iobroker.tibberlink/docu/calculatorStatesInverse.png) Поменяв местами true <-> false, вы получите true с низкой стоимостью в первой строке и true в высокая стоимость во второй строке (названия каналов не являются триггерами и по-прежнему свободны в выборе).

Внимание: для отдельных часов пиковой нагрузки, как в примере, вам также необходимо отрегулировать количество часов. Исходное значение: 5 -> Обратное (24-5) = 19 -> Вы получите истинный результат в течение 5 часов пик.

#### LTF-каналы
Расчет производится для «многодневных» данных. Поскольку у нас есть информация только на «сегодня» и «завтра» (доступна примерно после 13:00), временной диапазон фактически ограничен максимум 35 часами. Однако очень важно помнить об этом поведении, поскольку расчетный результат может измениться около 13:00, когда станут доступны новые данные о завтрашних ценах.

Чтобы наблюдать за этим динамическим изменением временного интервала для стандартного канала, вы можете выбрать ограниченный временной интервал (LTF), охватывающий несколько лет. Это особенно полезно для сценария «Лучший одночасовой LTF».

## Часовой
Этот адаптер использует библиотеки Sentry для автоматического сообщения разработчикам об исключениях и ошибках кода. Для получения более подробной информации и информации о том, как отключить отчеты об ошибках, обратитесь к разделу [Документация плагина Sentry](https://github.com/ioBroker/plugin-sentry#plugin-sentry)! Отчеты Sentry запускаются начиная с js-controller 3.0.

## Пожертвовать
<a href="https://www.paypal.com/donate/?hosted_button_id=F7NM9R2E2DUYS"><img src="https://raw.githubusercontent.com/Hombach/ioBroker.tibberlink/main/docu/bluePayPal.svg" height="40"></a> Если вам понравился этот проект или вы просто чувствуете щедрость, подумайте о том, чтобы купить мне пива. Ваше здоровье! :пиво:

## Changelog

! Note that missing version entries are typically dependency updates for improved security.

### 2.2.2 (2024-02-19)

-   (HombachC) simplify internal state handling
-   (HombachC) shorten home string in Calculator screen (#317)
-   (HombachC) fix feedback loop trap (#321)
-   (HombachC) add some tooltips to config screen (#317)

### 2.2.1 (2024-02-08)

-   (HombachC) fix edge case problems with defect feed data from Tibber server (#312)
-   (HombachC) bump dependencies

### 2.2.0 (2024-02-04)

-   (HombachC) add data points for BestHoursBlock results - period and average cost (#240)
-   (HombachC) fixed wrong error message texts
-   (HombachC) fix some possible edge cases in internal support functions
-   (HombachC) internal code docu optimization
-   (HombachC) bump dependencies

### 2.1.1 (2024-01-27)

-   (HombachC) fix reconnect error for Pulse feed (#300)
-   (HombachC) new error message handler
-   (HombachC) internal code docu optimization

### 2.1.0 (2024-01-21)

-   (HombachC) add repeatablity for LTF channels (#289)
-   (HombachC) tweak Smart Battery Buffer documentation

### 2.0.1 (2024-01-15)

-   (HombachC) modify timing in Tibber Pulse feed connect (#271)
-   (HombachC) bump dependencies

### 2.0.0 (2023-12-23)

-   (HombachC) BREAKING: dropped support for js-controller 3.x (#247)
-   (HombachC) diversificate Tibber server polls to prevent potential DDoS reactions (#252)
-   (HombachC) add data point for averageRemaining of todays prices (#254)
-   (HombachC) add 2 data points for last successfull update of today and tomorrow prices (#261)
-   (HombachC) year 2024 changes
-   (HombachC) fix small error in dynamic feed timing
-   (HombachC) bump dependencies

### 1.8.1 (2023-12-16)

-   (HombachC) add notice about changes in configuration

### 1.8.0 (2023-12-14)

-   (HombachC) implement optional disable of price pull (#232)
-   (HombachC) implement price categorization algorithm for battery buffer applications (#193)
-   (HombachC) Fix 2 errors in pull of prices tomorrow (#235, #232)
-   (HombachC) changed Tibber link in config

### 1.7.2 (2023-12-07)

-   (HombachC) implemented dynamic raise of feed reconnect (#225)
-   (HombachC) small bugfix in pricecalls
-   (HombachC) first changes for "smart battery buffer" (#193)
-   (HombachC) update typescript to 5.3.3

### 1.7.1 (2023-12-04)

-   (HombachC) added hint for consumption data in documentation (#223)
-   (HombachC) mitigate error handling (#217)
-   (HombachC) added description to object Features/RealTimeConsumptionEnabled (#224)
-   (HombachC) bump dependencies

### 1.7.0 (2023-11-30)

-   (HombachC) implement getting historical consumption data from Tibber Server (#163)
-   (HombachC) fix error in adapter unload
-   (HombachC) some code optimisations

### 1.6.1 (2023-11-26)

-   (HombachC) cleanup in documentation and translation handling

### 1.6.0 (2023-11-26)

-   (HombachC) fixed major bug in 1.5.0, not working calculator channels (#212)
-   (HombachC) implement limit calculations to a time frame (#153)
-   (HombachC) fix error of missing price data upon not working tibber server connect at adapter start (#204)
-   (HombachC) fixed possible error with wrong price date in multi home systems
-   (HombachC) fixed possible type error, notified by Sentry
-   (HombachC) added some documentation for inverse use of channels (#202)
-   (HombachC) added Sentry statistics
-   (HombachC) optimize translation handling
-   (HombachC) bump dependencies

### 1.5.0 (2023-11-13)

-   (HombachC) implement calculator channel names (#186)
-   (HombachC) fix error in cron jobs (#190)
-   (HombachC) remove not used calculator channel state objects (#188)
-   (HombachC) code optimizations
-   (HombachC) optimize translation handling

### 1.4.3 (2023-11-08)

-   (HombachC) fix possible type error in first calculator calls notified by Sentry
-   (HombachC) change state object description of production values (#167)
-   (HombachC) optimize pulse feed error message in case of error as object (#176)
-   (HombachC) preparations for calculator object names (#186)
-   (HombachC) bump dependencies

### 1.4.2 (2023-11-03)

-   (HombachC) complete rework of task scheduling for more precise pull timing (#149)
-   (HombachC) critical vulnerability fix for axios
-   (HombachC) fix debug message typos, code optimisations in calculator
-   (HombachC) fix type error in price average calculation notified by Sentry
-   (HombachC) fix error in update prices tomorrow - possible false positive

### 1.4.1 (2023-10-25)

-   (HombachC) implement forced update of all data after adapter restart (#155)
-   (HombachC) Bump actions/setup-node from 3.8.1 to 4.0.0 (#157)
-   (HombachC) remove node.js 16 actions - dependency updates

### 1.4.0 (2023-10-24)

-   (HombachC) implement min/max states (#131)
-   (HombachC) fix error with ignored calculator channel deaktivations (#143)
-   (HombachC) optimize translation handling, code cleanup

### 1.3.1 (2023-10-21)

-   (HombachC) fix initialisiation of channel states (#141)
-   (HombachC) change message "reconnect successful" to level info (#80)
-   (HombachC) documentation tweaks - dependency updates

### 1.3.0 (2023-10-20)

-   (HombachC) implement tibber calculator mode "best hours block" (#16)
-   (HombachC) handle empty calculator destination states - detected by sentry

### 1.2.0 (2023-10-18)

-   (HombachC) implement tibber calculator mode "best single hours" (#16)
-   (HombachC) changed i18n files to inline translations, single files aren't update compatible (#128)
-   (HombachC) fixed error in initial read of calculator states (#129)

### 1.1.2 (2023-10-15)

-   (HombachC) fix timing error in calculator

### 1.1.1 (2023-10-14)

-   (HombachC) fix error in startup of additional channels

### 1.1.0 (2023-10-14)

-   (HombachC) implement tibber calculator mode "best price" (#16)
-   (HombachC) precised pull times of current cost
-   (HombachC) reduced error messages (#80)
-   (HombachC) extend documentation
-   (HombachC) update adapter-core

### 1.0.0 (2023-10-05)

-   (HombachC) Increase to the first major release, as now a stable level is reached
-   (HombachC) Code cleanup

### Old Changes see [CHANGELOG OLD](CHANGELOG_OLD.md)

## License

GNU General Public License v3.0 only

Copyright (c) 2023-2024 C.Hombach <TibberLink@homba.ch>