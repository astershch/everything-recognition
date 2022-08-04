# everything-recognition
Скрипт для обнаружения и выделения различных объектов в потоке вебкамеры.


## Как установить

Python3 должен быть уже установлен. 
Затем используйте `pip` (или `pip3`, есть есть конфликт с Python2) для установки зависимостей:
```bash
pip install -r requirements.txt
```

## Как использовать

Для работы скрипта необходима подключенная веб-камера. Скрипт использует устройство по умолчанию.

Для обнаружения определенного обьекта необходимы определенные каскады Хаара. 
Примеры находятся в папке [haarcascades](./haarcascades).

Перед запуском скрипта необходимо изменить его [конфигурацию](./config.py) в зависимости от обьектов распознавания.

Параметры конфигурации:
- `path` - путь до каскада Хаара для распознаваемого объекта
-  `color` - цвет рамки по модели RGB, в которой будет находиться распознанный объект
-  `draw` - флаг отображения рамки (True - отображать)

Например, конфигурация для распознавания фронтально расположенного лица и в профиль (в профиль рамка не отображается):
```python
CASCADES = {
    "Face front": {
        "path": "haarcascades/faces/haarcascade_frontalface_default.xml",
        "color": (255, 0, 0),
        "draw": True
    },
    "Face profile": {
        "path": "haarcascades/faces/haarcascade_profileface.xml",
        "color": (255, 0, 0),
        "draw": False
    }
}
```

Запуск скрипта:

```
python run.py
```

После запуска скрипт создает окно, в котором будут распознаваться объекты в потоке веб-камеры в соотвествии с заданной конфигурацией.

При удачном распознавании и выставленном флаге `draw` объект будет выделен прямоугольной рамкой с соответствующим цветом.

Для закрытия окна веб-камеры нужно нажать клавишу с буквой `q`.

