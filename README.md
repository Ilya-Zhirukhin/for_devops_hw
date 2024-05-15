# for_devops_hw_1

Создайте новый файл с расширением .sh, например, create_user_dirs.sh, и скопируйте в него код скрипта.

Откройте терминал и перейдите в директорию, где находится файл скрипта.

Сделайте файл скрипта исполняемым, выполнив команду:

chmod +x create_user_dirs.sh
Запустите скрипт одним из следующих способов:

Если хотите указать путь к корневому каталогу через ключ "-d", выполните:

./create_user_dirs.sh -d /path/to/root/directory
Замените /path/to/root/directory на фактический путь к корневому каталогу, где должны быть созданы директории пользователей.

Если не указываете ключ "-d", скрипт запросит у вас путь к корневому каталогу через диалоговое окно. Выполните:

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

![image](https://github.com/Ilya-Zhirukhin/for_devops_hw/assets/99948155/7a56fab9-6ef4-462a-82cb-594eb9903877)

# for_hw_devops_2



Разберем playbook по частям:

hosts: remote_server указывает на удаленный сервер, на котором будут выполняться задачи.

become: yes позволяет выполнять задачи с правами суперпользователя.

В разделе vars определены переменные:

username: имя пользователя, которого нужно создать.
ssh_key: публичный SSH-ключ для авторизации пользователя. Здесь используется функция lookup для чтения содержимого файла с ключом.
directory_path: путь к директории, которую нужно создать.
Задача "Create user" создает пользователя с указанным именем.

Задача "Add SSH key for user" добавляет публичный SSH-ключ для авторизации пользователя.

Задача "Disable password authentication" отключает авторизацию по паролю в конфигурационном файле SSH. При изменении файла вызывается handler "Restart SSH" для перезапуска службы SSH.

Задача "Create directory" создает директорию с указанным путем и правами для созданного пользователя.

В разделе handlers определен handler "Restart SSH", который перезапускает службу SSH при необходимости.

Перед запуском playbook убедитесь, что:

У вас есть (inventory) с указанием удаленного сервера remote_server.
На локальной машине, откуда запускается playbook, есть приватный SSH-ключ, соответствующий публичному ключу ssh_key.
Запустите playbook командой:

ansible-playbook -i inventory.ini playbook.yml
После выполнения playbook на удаленном сервере будет создан пользователь, настроена авторизация по SSH-ключу, отключена авторизация по паролю и создана директория с указанными правами.

# for_hw_devops_3

Создание структуры роли

каталог роли и вложенные каталоги:
mkdir -p ansible-role-user-setup/{tasks,vars,defaults,meta,molecule/default}
cd ansible-role-user-setup

файлы для задач, переменных, и т.д.:
touch tasks/main.yml
touch vars/main.yml
touch defaults/main.yml
touch meta/main.yml
touch molecule/default/molecule.yml
touch molecule/default/converge.yml
touch molecule/default/verify.yml

Инициализация Molecule и запуск тестов:

molecule init scenario --role-name ansible-role-user-setup --driver-name docker
molecule test

в итоге создаем базовую конфигурацию для роли Ansible, которая создаёт пользователя, настраивает SSH авторизацию по ключам, отключает аутентификацию по паролю и создаёт директорию в /opt/. Molecule поможет вам тестировать роль в контейнере Docker, что упрощает разработку и тестирование Ansible ролей.



# for_hw_devops_4

docker build -t zhiruhin_ii_image_$(date +%F) .
![image](https://github.com/Ilya-Zhirukhin/for_devops_hw/assets/99948155/0298011f-56fc-48a8-808c-2f0ab54838f8)
слои и размер на диске
docker history zhiruhin_ii_umage2024-05-15
![image](https://github.com/Ilya-Zhirukhin/for_devops_hw/assets/99948155/4dfe5cdb-b114-4eac-ad78-d57122118c78)



