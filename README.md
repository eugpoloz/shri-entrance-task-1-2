# Задание 1 — найди ошибки

В этом репозитории находится выполненное тестовое задание "Найди ошибки" для [14-й Школы разработки интерфейсов](https://academy.yandex.ru/events/frontend/shri_msk-2018-2) (осень 2018, Москва, Санкт-Петербург, Симферополь).

## Запуск

```
npm i
npm start
```

## Выполнение задания

1. Первое, что я сделала после `npm i` — это провела рекомендованный `npm audit fix`, чтобы исправить две критические уязвимости.

2. `npm run start` сработал с ошибкой. Заход в консоль показал, что ошибка вылезает на `initMap`. Как оказалось, `initMap` неверно импортировался — я, быстро пробежавшись взглядом по кодовой базе, предпочла вместо экспорта по умолчанию использовать обычный.

3. Для приведения codestyle к единству и минимальных заморочек при этом я воспользовалась локальным prettier. 😀

4. Ошибок сборки больше не было, но карта по-прежнему не отобразилась. Инспектор показал, что это потому, что у карты нет высоты. Задать `html`, `body` и `#map` высоту (и на всякий случай ширину) решило проблему. Раз максимальной совместимости со старыми браузерами в задаче не требуется, я воспользовалась `vw` и `vh`.

5. Точки на карте все еще не показываются. API Яндекс.Карт говорит, что просто создать `ObjectManager` недостаточно (что логично): его надо еще и добавить в карту. Добавляем `myMap.geoObjects.add(objectManager);` в конструкторе карты.
