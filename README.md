# Bird4Static
Здесь выложены файлы для работы bird4 с сервисом antifilter.download

Без BGP, с обычным обновлением раз в сутки, с возможностью внесения пользоватеельских правил.

Предназначено для роутеров Keenetic с установленным на них entware

Установка:
1) Зайти по ssh в среду entware
2) Выполнить:

  opkg install git git-http
  
  git clone https://github.com/DennoN-RUS/Bird4Static.git
  
  chmod +x /opt/root/Bird4Static/install.sh
  
  /opt/root/Bird4Static/install.sh
  
3) Далее во время выполнения скрипта постребуется ввести имя интерфейса провайдера и интерфейса VPN. А потом имя интерфейса VPN из прошивки кинетика. Все данные будут выводиться в консоль перед вводом, так что необходимо только скопировать нужные имена и вставить в консоль
4) После выполнения установки роутер получит маршрутизацию через впн до нужных ресурсов

ОПЦИОНАЛЬНО:

5) Так же можно принудительно указать ресурсы которые надо пустить через VPN или провайдера. Для этого нужно отредактировать файлы:

  vi /opt/etc/bird4-isp.txt - для перенаправления трафика через провайдера
  
  vi /opt/etc/bird4-vpn.txt - для перенаправления трафика через VPN
  
  После редактирования надо запустить скрипт обновления
  
  /opt/etc/cron.daily/add-bird4_routes.sh
  
6) Если нужно пустить трафик только до ресурсов добавленных в файлы, которые указаны выше, без общего списка c antifilter.download, то нужно закомментровать, т.е. поставить знак # в начале строки URL0=https://antifilter.download/list/allyouneed.lst в файле /opt/etc/cron.daily/add-bird4_routes.sh. Потом нужно заполнить хотя бы один файл из п.5 и выполнить

/opt/etc/cron.daily/add-bird4_routes.sh

Более подробно что и как расписано здесь:

https://forum.keenetic.net/topic/8577-%D0%BE%D0%B1%D1%85%D0%BE%D0%B4-%D0%B1%D0%BB%D0%BE%D0%BA%D0%B8%D1%80%D0%BE%D0%B2%D0%BE%D0%BA-%D1%81-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%D0%BC-bird4/
git clone https://github.com/DennoN-RUS/Bird4Static.git
