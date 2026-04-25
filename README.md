# DPN-client
Deeper Network client (for testing purposes only)

### Содержимое оригинального пакета DEB
- /usr/bin/dpn (ссылка на /lib/dpn/DPN)
- /usr/lib/dpn/
- /usr/share/applications/dpn.desktop
- /usr/share/doc/dpn/
- /usr/share/lintian/overrides/dpn
- /usr/share/pixmaps/dpn.png

Первый запуск - требует root для запуска бэкэнда: `systemctl start dpn-app.service`  
**Локация:** /etc/systemd/system/dpn-app.service

[Тестовый RPM только для тестирования на виртуальных машинах...](https://drive.google.com/drive/folders/1axiXNtRGGtPx1G1GgATTWJBfGoAR-azZ?usp=drive_link)

![](https://github.com/AKotov-dev/DPN-client/blob/main/Snapshot_2026-04-24_08-14-051.png) ![](https://github.com/AKotov-dev/DPN-client/blob/main/Snapshot_2026-04-25_09-23-531.png)

### Тестирование
Три режима: Умная маршрутизация (Режим ИИ - понравился.... маркетинг, конечно, но красиво), Полная маршрутизация и Прямая маршрутизация (без VPN). Соединяется через раз, подключается медленно, всё зависит от наличия работающих в сети. Создаёт интерфейс `dpn0`, как в Amnezia примерно.

Клиент вроде не мусорный: в idle не гадит (Wireshark), единственный сервис создаёт динамически (запрос, см. выше). Вход/Регистрация - Почта (лучше Proton). В общем и целом первое впечатление - хорошее. Пока держим в `QEMU`, но клиент вроде юзабельный.

Установка - на одно устройство, ID (возможно) привязыавется через конфиги `~/.config/DPN`. Вход на новом устройстве **только после выхода с первого**, таймаут выяснить не удалось. На новой VM лучше сразу очистить `~/.config/DPN` и перезайти.

Подключение (особенно первое) проходит долго, скорость подключения удовлетворительная.

Для энтузиастов из DEB собран RPM (проект *.prj для RPMCreator см. в репе). Если есть что сказать - пишите в issues. ))
