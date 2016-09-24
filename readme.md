## Панорама хакерспейса

В качестве движка использован открытый [pannellum](https://github.com/mpetroff/pannellum/).
Используемые технологии: HTML5, CSS3, JavaScript и WebGL.

Панорама имеет ограничение в 4096px на файл.

### TODO:
- [ ] Переснять и свести актуальную панораму (включая пол и потолок, чтобы pannelum не сворачивал изображение)
- [ ] Разделить панораму на части, чтобы уменьшить трафик
- [ ] Добавить ссылки на проекты в панораму
- [ ] Опубликовать на https://hackerspace.by/

### Разметка

На панораме можно разместить различного рода указатели.
Для определения координат указателя можно включить режим отладки `hotSpotDebug=true`, при котором по клику на панораме в консоль отладки (FireBug) будут выводиться координаты (`pitch` и `yaw`). В поле `text` задаётся текст всплывающей подсказки.

В зависимости от значения поля `type` будет меняться изображение и функциональность значка

- `info` - Информация (значёк 'i') - кликабельный тултип.
```json
"hotSpots": [
    {
        "pitch": 14.1,
        "yaw": 1.5,
        "type": "info",
        "text": "Hackerspace",
        "URL": "https://hackerspace.by/"
    }
]
```

  В поле `URL` можно указать ссылку которая открывается при клике.

  [Пример справочных указателей](https://pannellum.org/documentation/examples/tour/)


- `scene` - Указатель на другую локацию (стрелка)
```json
"hotSpots": [
                {
                    "pitch": -2.1,
                    "yaw": 132.9,
                    "type": "scene",
                    "text": "Главное помещение",
                    "sceneId": "main room",
                    "targetYaw": -23,
                    "targetPitch": 2
                }
            ]
```

  В поле `sceneId` должен быть указан идентификатор нужной карты из списка сцен.

  [Пример тура](https://pannellum.org/documentation/examples/tour/)

### Решение проблем

#### Сворачивание панорамы

Если панорама не сферическая, нужно выставлять параметр [vaov](https://pannellum.org/documentation/examples/partial-panorama/), иначе панораму сворачивает в сферу. Примерно так
```html
vaov=54.15
```
Спасибо @Jekhor
