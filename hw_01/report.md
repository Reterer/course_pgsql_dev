### Домашнаяя работа №1

Выполнил: Суханов Е.А.

#### 1. Создание ВМ с PostgreSQL

Развернул PostgreSQL в ЯО.

1. Создание ВМ. Создал и запустил ВМ через веб-интерфейс.

2. Установка yc
```sh
# https://yandex.cloud/ru/docs/cli/operations/install-cli
curl -sSL https://storage.yandexcloud.net/yandexcloud-yc/install.sh | bash
yc init
```

3. Подключение к вм
```sh
yc compute ssh --id fv4rife88j2hau3rn6j1 --identity-file ~/.ssh/ya --login sukhanov_egor
```

4. Установка PostgreSQL
```sh
# https://www.postgresql.org/download/linux/ubuntu/
sudo apt install -y postgresql-common
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh
sudo apt install postgresql-17
```

#### 2. Загрузка Тайских перевозок в минимальном варианте

```sh
sudo su postgres && cd ~
wget https://storage.googleapis.com/thaibus/thai_small.tar.gz && tar -xf thai_small.tar.gz && psql < thai.sql
```

#### 3. Подсчёт кол-ва поездок

```sh
postgres=# \c thai
You are now connected to database "thai" as user "postgres".

thai=# select count(*) from book.tickets;
  count  
---------
 5185505
(1 row)

thai=# 
```