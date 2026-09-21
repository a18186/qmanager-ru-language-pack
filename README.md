# Russian Language Pack for QManager

Русский языковой пакет для QManager (Quectel RM520N-GL).

## Скачать

- [Полный набор для Windows (ZIP)](https://github.com/a18186/qmanager-ru-language-pack/releases/download/language-packs/qmanager-ru-langpack-v2026.09.17.zip)
- [Языковой пакет для QManager (.tar.gz)](https://github.com/a18186/qmanager-ru-language-pack/releases/download/language-packs/qmanager-ru-v2026.09.17.tar.gz)

## Установка (Windows + ADB)

1. Скачайте ZIP-архив по ссылке выше.
2. Распакуйте в любую папку.
3. Подключите модем к ПК по USB (ADB должен работать).
4. Запустите `install.bat` → дождитесь «Установка завершена».
5. Откройте QManager → **System Settings → Languages** → **Русский**.

## Установка (вручную, через ADB)

Если install.bat не работает — установите вручную:

```
adb push files /tmp/ru-langpack/files
adb push install.sh /tmp/ru-langpack/install.sh
adb shell sed -i "s/\r$//" /tmp/ru-langpack/install.sh
adb shell sh /tmp/ru-langpack/install.sh
```

Затем перезапустите веб-сервер:

```
adb shell systemctl restart lighttpd
```


## Требования

- Модем Quectel RM520N-GL с установленным QManager v0.1.16+
- Разблокированный ADB на модеме
- ADB на ПК (в PATH)

## Удаление

```
adb shell rm -rf /usrdata/qmanager/locales-packs/ru
adb shell rm -rf /usrdata/qmanager/www/locales-packs/ru
adb shell systemctl restart lighttpd
```

Или через веб-интерфейс: **System Settings → Languages → значок корзины**.


## Проверка
adb shell jq empty /usrdata/qmanager/www/locales-packs/ru/common.json


Если команда молча вернула приглашение — пакет установлен корректно.

## Параметры пакета

| Поле | Значение |
|---|---|
| Код языка | `ru` |
| Версия | 2026.09.17 |
| Совместимость | QManager v0.1.16+ |
| Полнота | 100% (6 namespace-файлов) |
| Формат | `_pack.json` + JSON-файлы |

## Автор

[@a18186](https://github.com/a18186)

## Ссылки

- [QManager (оригинал)](https://github.com/dr-dolomite/QManager-RM520N)
- [Manifest](./manifest.json)
