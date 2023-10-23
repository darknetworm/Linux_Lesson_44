# Linux_Lesson_44
## PostgreSQL
### Описание репозитория

Лабораторный стенд для СУБД PostgreSQL, состоящий из основного сервера, сервера репликации и сервера создания и хранения резервных копий barman. 

- **Vagrantfile** - создает три виртуальные машины (основной сервер - node1, сервер репликации - node2 и сервер резервного копирования - barman) на основе Ubuntu 20.04 с СУБД PostgreSQL версии 16.
- **provision.yml** - основной файл Ansible playbook для установки и настройки виртуальных машин стенда.
> [!IMPORTANT]
> Для настройки СУБД PostgreSQL с помощью Ansible playbook на хостовую машину необходимо установить библиотеку для работы с СУБД:
> 
    ansible-galaxy collection install community.postgresql
- **hosts** - файл для доступа к виртуальным машинам из playbook.
- директория **/templates** содержит конфигурационные файлы для серверов стенда.
- в директории **/roles**  находятся конфигурационные файлы для настройки настройки стенда с помощью Ansible:
  - **setup_sql_servers** - общие настройки серверов PostgreSQL;
  - **setup_node1** - настройки основного сервера PostgreSQL;
  - **setup_node2** - настройки серевера репликации;
  - **setup_barman** - настройки основного сервера и сервера barman для резервного копирования данных.

 ---
 ### Проверка работоспособности стенда

 ![1_node1](https://github.com/darknetworm/Linux_Lesson_44/assets/82410807/eef452f8-c8e6-4794-adfb-eb67ebb633ce)

![1_node2](https://github.com/darknetworm/Linux_Lesson_44/assets/82410807/43c44157-9674-492a-a846-7189f52821c5)

![1_barman](https://github.com/darknetworm/Linux_Lesson_44/assets/82410807/360ad3e3-0a44-4d58-bdef-5156c8bd87a7)

![2_node1](https://github.com/darknetworm/Linux_Lesson_44/assets/82410807/cce68b20-76ee-4e09-a86c-bac3d69fd04f)

![2_barman](https://github.com/darknetworm/Linux_Lesson_44/assets/82410807/783b9207-4c0d-4a03-aa62-9ac329d1360d)

