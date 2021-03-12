# Android section

## Links

- [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) - adb


## adb сервер

    adb devices -l
    adb kill-server


## clean apps

- [Как удалить «неудаляемые» приложения со смартфона](https://habr.com/ru/company/vdsina/blog/528550/) - via adb

_список нужных apps_

    adb shell pm list packages | grep 'music'

_удаление_

    adb shell pm uninstall -k --user 0 com.qrd.zerobalancehelper

_команды_

`adb shell pm list users` - список пользователей

`adb shell df -h` - любая linux команда

