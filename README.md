# for_devops_hw_1

Создайте новый файл с расширением .sh, например, create_user_dirs.sh, и скопируйте в него код скрипта.

Откройте терминал и перейдите в директорию, где находится файл скрипта.

Сделайте файл скрипта исполняемым, выполнив команду:

chmod +x create_user_dirs.sh
Запустите скрипт одним из следующих способов:

Если вы хотите указать путь к корневому каталогу через ключ "-d", выполните:

./create_user_dirs.sh -d /path/to/root/directory
Замените /path/to/root/directory на фактический путь к корневому каталогу, где должны быть созданы директории пользователей.

Если вы не указываете ключ "-d", скрипт запросит у вас путь к корневому каталогу через диалоговое окно. Выполните:

./create_user_dirs.sh
Затем введите путь к корневому каталогу при появлении запроса.

Скрипт создаст директории для каждого пользователя в указанном корневом каталоге с правами доступа 755 и установит соответствующего пользователя в качестве владельца каждой директории.

Лог выполнения скрипта будет выводиться как в терминал (stdout), так и записываться в файл create_user_dirs.log в той же директории, где находится скрипт.

Пример использования:

./create_user_dirs.sh -d /home/user/project
или

./create_user_dirs.sh
Введите путь к корневому каталогу: /home/user/project
После выполнения скрипта вы увидите созданные директории пользователей в указанном корневом каталоге, и сможете просмотреть лог выполнения в файле create_user_dirs.log.
