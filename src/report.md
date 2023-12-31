## Part 1. Установка ОС

1. Проверить версию Ubuntu:<br>
   ![part 1](screenshots/1.png)<br>

## Part 2. Создание пользователя

1. Создать пользователя и добавить его в группу adm:<br>
   ![part 2.1](screenshots/2.png)<br>
2. Вывести список пользователей (в конце):<br>
   ![part 2.2](screenshots/3.png)<br>

## Part 3. Настройка сети ОС

1. Задать имя машины вида user-1:<br>
   ![part 3.1](screenshots/4.png)<br>
2. Установить временную зону, соответствующую текущему местоположению, и вывести информации о времени:<br>
   ![part 3.2](screenshots/5.png)<br>
3. Установить набор сетевых интерфейсов:<br>
   ![part 3.3](screenshots/6.png)<br>
4. Вывести информацию о сетевых интерфейсах:<br>
   ![part 3.4](screenshots/7.png)<br>
   - **lo (loopback device)** - виртуальный интерфейс, присутствующий по умолчанию в любом Linux. Он используется для отладки сетевых программ и запуска серверных приложений на локальной машине. С этим интерфейсом всегда связан адрес 127.0.0.1. У него есть dns-имя – localhost.<br>
5. Получить ip-адрес устройства от DHCP сервера<br>
   ![part 3.5](screenshots/8.png)<br>
   - ip адрес устройства указан после **bound to**<br>
   - **DHCP** - Dynamic Host Configuration Protocol<br>
6. Получить внешний ip-адрес<br>
   ![part 3.6](screenshots/9.png)<br>
7. Вывести внутренней адрес шлюза (ip-адрес по умолчанию)<br>
   ![part 3.7](screenshots/10.png)<br>
8. Задать статичные настройки ip, gw, dns<br>
   ![part 3.8](screenshots/11.png)<br>
9. Применить изменения в netplan и перезагрузиться<br>
   ![part 3.9](screenshots/12.png)<br>
10. Проверить соответствия адресов адресам, указанным в предыдущем пункте<br>
    ![part 3.10](screenshots/13.png)<br>
11. Пропинговать удаленные хосты 1.1.1.1 и ya.ru<br>
    ![part 3.11](screenshots/14.png)<br>

## Part 4. Обновление ОС

1. Обновить системные пакеты до последней на момент выполнения задания версии<br>
   ![part 4](screenshots/15.png)<br>

## Part 5. Использование команды sudo

1. **sudo** - позволяет временно поднимать привилегии и выполнять команды администрирования с максимальными правамии.<br>
2. Добавить пользователя, созданного в Part 2, в группу с привилегиями sudo<br>
   ![part 5.1](screenshots/16.png)<br>
3. Поменять hostname ОС от имени пользователя, созданного в пункте Part 2 (используя sudo).<br>
   ![part 5.2](screenshots/17.png)<br>

## Part 6. Установка и настройка службы времени

1. Вывести время часового пояса<br>
   ![part 6.1](screenshots/18.png)<br>
2. Вывод команды timedatectl show<br>
   ![part 6.2](screenshots/19.png)<br>

## Part 7. Установка и использование текстовых редакторов

1. Сохранить никнейм<br>
   1. **VIM** - для записи никнейма необходимо войти в режим вставки ("I"). Для сохранения изменений, необходимо перейти в стандартный режим (ESC) и прописать :wq test_vim.txt.<br>
      ![part 7.1](screenshots/20.png)<br>
   2. **NANO** - для сохранения изменений необходимо нажать ^O, после чего ввести имя файла. Выйти с помощью ^X.<br>
      ![part 7.2](screenshots/21.png)<br>
   3. **JOE** - для сохранения изменений необходимо нажать :KX и ввести имя файла<br>
      ![part 7.3](screenshots/22.png)<br>
2. Заменить никнейм на строку "21 School 21", закрыть файл без изменений<br>
   1. **VIM** - для закрытия файла без изменений войти в стандартный режим (ESC) и прописать :q!<br>
      ![part 7.4](screenshots/23.png)<br>
   2. **NANO** - для закрытия файла без изменений ^X -> N <br>
      ![part 7.5](screenshots/24.png)<br>
   3. **JOE** - для закрытия файла без изменений ^C -> y<br>
      ![part 7.6](screenshots/25.png)<br>
3. Отредактировать файл, используя функции поиска по содержимому файла и замены слова на любое другое<br>
   1. **VIM**<br>
      - для поиска содержимого: /текст<br>
         ![part 7.7](screenshots/26.png)<br>
      - для замены: :s/текст для замены/замена<br>
         ![part 7.8](screenshots/27.png)<br>
   2. **NANO**<br>
      - для поиска содержимого: ^W -> текст<br>
         ![part 7.9](screenshots/28.png)<br>
      - для замены: : ^\ -> текст для замены -> замена -> Y<br>
         ![part 7.10](screenshots/29.png)<br>
   3. **JOE**<br>
      - для поиска содержимого: ^K F -> текст для замены -> I<br>
         ![part 7.11](screenshots/30.png)<br>
      - для замены: : ^K F -> текст для замены -> R -> замена -> Y<br>
         ![part 7.12](screenshots/31.png)<br>

## Part 8. Установка и базовая настройка сервиса SSHD

1. Установить пакет OpenSSH server:<br>
   `sudo apt install openssh-server`<br>
2. Добавить автостарт службы при загрузке системы:<br>
   `sudo systemctl start ssh`<br>
3. Проверить работоспособность утилиты:<br>
   `ssh localhost`<br>
4. Перенастроить службу SSHd на порт 2022<br>
   - Перед модификацией конфигурационного файла создать резеврную копию:<br>
     `sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-defaults`<br>
   - Открыть файл конфигурации:<br>
     `sudo vim /etc/ssh/sshd_config`<br>
   - Изменить порт на 2022:<br>
     ![part 8.1](screenshots/32.png)<br>
5. Используя команду ps, показать наличие процесса sshd:<br>
   `ps -ef | grep sshd`<br>
   **ps** - выводит список текущих процессов;<br>
   **-e** - выбрать все процессы;<br>
   **-f** - показывает полную информацию;<br>
   **grep ssh** - вывод процессов, которые содержат строку ssh;<br>
   **ps -ef | grep sshd** - показывает полную информацию по процессам, содержащим строку sshd;<br>
   ![part 8.2](screenshots/33.png)<br>
   Перезагрузить систему:<br>
   `sudo reboot`
6. Вывод команды netstat -tan:<br>
   ![part 8.3](screenshots/34.png)<br>
   **-tan**:<br>
   **-t** - отображать TCP подключения;<br>
   **-a** - показать состояние всех сокетов;<br>
   **-n** - показывать сетевые адреса как числа;<br>
   **Proto** - Содержит тип протокола<br>
   **Recv-Q** - Счётчик байтов не скопированных программой пользователя из этого сокета.<br>
   **Send-Q** - Счётчик байтов, не подтверждённых удалённым узлом.<br>
   **Local Address** - Адрес и номер порта локального конца сокета.<br>
   **Foreign Address** - Адрес и номер порта удалённого конца сокета.<br>
   **State** - Состояние сокета.<br>
   **LISTEN** Сокет ожидает входящих подключений.<br>
   **SYN_SENT** Сокет, находящийся в режиме активной попытки установки подключения.<br>
   **0.0.0.0** - это немаршрутизируемый адрес IPv4, который используется в качестве адреса по умолчанию или адреса-заполнителя.

## Part 9. Установка и использование утилит top, htop

1. Использовать утилиту **top**:<br>
   - uptime: 26 min;<br>
   - количество авторизованных пользователей: 1;<br>
   - общую загрузку системы: 0.00, 0.00, 0.00;<br>
   - общее количество процессов: 118;<br>
   - загрузку cpu: 0.0 us, 0.0 sy, 0.0 ni, 100.0 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st;<br>
   - загрузку памяти: 7947.5 total, 7446.3 free, 166.4 used, 334.8 buff/cache;<br>
   - pid процесса занимающего больше всего памяти: 1;<br>
   - pid процесса, занимающего больше всего процессорного времени: 425;<br>

   ![part 9.1](screenshots/35.png)<br>

2. Использовать утилиту htop:<br>

   - отсортировать по PID:<br>
     ![part 9.2](screenshots/36.png)<br>
   - отсортировать по PERCENT_CPU:<br>
     ![part 9.3](screenshots/37.png)<br>
   - отсортировать по PERCENT_MEM:<br>
     ![part 9.4](screenshots/38.png)<br>
   - отсортировать по TIME:<br>
     ![part 9.5](screenshots/39.png)<br>
   - отсортировать для процесса sshd:<br>
     ![part 9.6](screenshots/40.png)<br>
   - процесс syslog, найденный через поиск:<br>
     ![part 9.7](screenshots/41.png)<br>
   - добавить вывод hostname, clock и uptime<br>
     ![part 9.7](screenshots/42.png)<br>

## Part 10. Использование утилиты fdisk

1. Запустить команду `sudo fdick -l`<br>
   ![part 10](screenshots/43.png)<br>

- Записать в отчете название жесткого диска, его размер и количество секторов, а также размер swap: Disk /dev/sda: 20 Gib, 2147836480 bytes, 41943040 sectors <br>

## Part 11. Использование утилиты df

1. Запустить команду `df`:<br>
   ![part 11.1](screenshots/44.png)<br>

   - размер раздела: 10218772 Кб;<br>
   - размер занятого пространства: 2725108 Кб;<br>
   - размер свободного пространства: 6952992 Кб;<br>
   - процент использования: 29%;<br>

2. Запустить команду `df -Th`:<br>
   ![part 11.2](screenshots/45.png)<br>
   - размер раздела: 9,8 Гб;<br>
   - размер занятого пространства: 2,6 Гб;<br>
   - размер свободного пространства: 6,7 Гб;<br>
   - процент использования: 29%;<br>
   - Тип файловой системы: ext4;<br>

## Part 12. Использование утилиты du

1. Запустить команду `du`.<br>
   ![part 12.1](screenshots/46.png)<br>
2. Вывести размер папок /home, /var, /var/log (в байтах, в человекочитаемом виде):<br>
   - `du -h /home`:<br>
     ![part 12.2](screenshots/47.png)<br>
   - `du -h /var`:<br>
     ![part 12.3](screenshots/48.png)<br>
   - `du -h /var/log`:<br>
     ![part 12.4](screenshots/49.png)<br>
3. Вывести размер всего содержимого в /var/log (не общее, а каждого вложенного элемента, используя \*)<br>
   - `du -h /var/log/*`:<br>
     ![part 12.5](screenshots/50.png)<br>

## Part 13. Установка и использование утилиты ncdu

1. Установить утилиту ncdu:
   - `sudo apt install ncdu`<br>
     ![part 13.1](screenshots/51.png)<br>
2. Вывести размер папок /home, /var, /var/log:<br>
   - `ncdu /home`:<br>
     ![part 13.2](screenshots/52.png)<br>
   - `ncdu /var`:<br>
     ![part 13.3](screenshots/53.png)<br>
   - `ncdu /var/log`:<br>
     ![part 13.4](screenshots/54.png)<br>

## Part 14. Работа с системными журналами

1. Последняя авторизация:<br>
   ![part 14.1](screenshots/55.png)<br>

2. Перезапуск OpenSSH Server:<br>
   ![part 14.1](screenshots/56.png)<br>

## Part 15. Использование планировщика заданий CRON

1. Используя планировщик заданий, запускать команду uptime через каждые 2 минуты:<br>

   `vim crontab -e`<br>

   ![part 15.1](screenshots/57.png)<br>

   - uptime каждые 2 минуты:<br>
     ![part 15.2](screenshots/58.png)<br>

2. Вывести список задач:<br>
   `crontab -l`<br>
   ![part 15.3](screenshots/59.png)<br>
3. Удалить все задания из планировщика заданий:<br>
   `crontab -r`<br>
4. Вывести список текущих задач:<br>
   ![part 15.4](screenshots/60.png)<br>
