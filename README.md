# DPN-client
Deeper Network client  
HomePage: [macOS, Windows, Linux, App Store, Android](https://dpn.deeper.network/)

**Содержимое оригинального пакета DEB**

- /usr/bin/dpn (ссылка на /lib/dpn/DPN)
- /usr/lib/dpn/
- /usr/share/applications/dpn.desktop
- /usr/share/doc/dpn/
- /usr/share/lintian/overrides/dpn
- /usr/share/pixmaps/dpn.png

[RPM-пакет для Mageia-9/10, Fedora. etc...](https://drive.google.com/drive/folders/1axiXNtRGGtPx1G1GgATTWJBfGoAR-azZ?usp=drive_link)

**Зависимости** (не включены в пакет, уже есть в системе):
```
libgtk+3.0 lib64notify4 lib64nss3 xdg-utils "typelib(Atspi)" libdrm libgbm lib64xcb-dri3_0 glib2 gvfs
```
Первый запуск требует `root` для бэкэнда (запрос `pkexec`): `systemctl start dpn-app.service`  
  
**Расположение сервиса:** /etc/systemd/system/dpn-app.service

![](https://github.com/AKotov-dev/DPN-client/blob/main/Snapshot_2026-04-24_08-14-051.png) ![](https://github.com/AKotov-dev/DPN-client/blob/main/Snapshot_2026-04-25_09-23-531.png)

### Тестирование
**Три режима** 
- Умная маршрутизация (режим ИИ понравился... маркетинг конечно, но красиво)
- Полная маршрутизация (одна нода)
- Прямая маршрутизация (без VPN, напрямую)

Соединяется через раз, подключается медленно, всё зависит от наличия работающих в сети. Создаёт интерфейс `dpn0`, как в Amnezia примерно.

Клиент вроде не мусорный: в idle не гадит (Wireshark), единственный сервис создаёт динамически (запрос, см. выше). Вход/Регистрация - Почта (лучше Proton). В общем и целом первое впечатление - хорошее. Клиент юзабельный.

**Файлы конфигурации и кеш:** `~/.config/DPN`. Если переподключаемся на новой VM - лучше сразу очистить `~/.config/DPN` и перезапустить соединение.

В **Умном режиме** параллельно просматривает доступные ноды/узлы выбранных стран, в случае необходимости меняет локацию и протокол.

Внутри страны ходит напрямую, поэтому сайты вроде "Госуслуг", "Ozon", "Wildberries" и т.п. VPN не видят.

[DNS Leak](https://browserleaks.com/dns) не наблюдается (Mageia).

**Важно:** Если используется `DNSCrypt` или DNS провайдера, нужно прописать обычные DNS в настройках карты, например Google/Cloudflare/Cisco/etc. В результате при подключении должен быть **Тип NAT: Port Restricted NAT**. Сложные цепочки DNS - плохо для `p2p/VPN/mesh`.

Подключение (особенно первое) проходит долго (2-10 мин.), скорость подключения удовлетворительная.  
  
Для энтузиастов из DEB собран RPM. Проект [DPN.prj](https://github.com/AKotov-dev/DPN-client/blob/main/DPN.prj) для [RPMCreator](https://github.com/AKotov-dev/RPMCreator) см. в репе.
