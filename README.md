# Пример приложения на solidus

1. Скачайте данный репозиторий

1. Перейдите в корень репозитория
    
    ```cd solidus-example ```

1. В корне проекта создайте файл с переменными среды *.env* cледующего содержания

    ```
    DATABASE_NAME=solidus_example_development
    DATABASE_USER=solidus
    DATABASE_PASSWORD=123456
    DATABASE_HOST=database
    ```

1. Имея в распоряжении файл docker-compose.yml, вы можете создать ваши службы с помощью команды docker-compose up и создать исходные записи базы данных. Также вы можете проверить сохранение данных, останавливая работу контейнеров и удаляя их с помощью docker-compose down, а затем воссоздавая их. Во-первых, необходимо выполнить сборку образов и создать службы, запустив `docker-compose up` с флагом -d, который будет запускать контейнеры в фоновом режиме:
    ```
    docker-compose up -d
    ```
1.  Cоздайте базу данных в контейнере
    ```
    docker-compose exec app bundle exec rake db:create db:migrate
    ```
1.  Сконфигурируйте приложение 
    ```
    docker-compose exec app bundle exec bin/rails g solidus:install
    ```
1.  Для остановки приложения и удаления контейнеров используйте команду
    ```
    docker-compose down
    ```

