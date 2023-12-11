# Задание №1

Веб-приложение на Python с уязвимостями XSS, IDOR, SQL Injection, OS command injection, Path Traversal, Brute force

## Установка

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
   
## Уязвимости

XSS:
```
 http://127.0.0.1:5000/xss?input=<script>alert('XSS')</script>
```
IDOR:
```
http://127.0.0.1:5000/profile/1
http://127.0.0.1:5000/profile/2
```
SQL Injection:
```
http://127.0.0.1:5000/search?input=' OR '1'='1'
```

OS Command Injection:
```
http://127.0.0.1:5000/ping?hostname=localhost | dir
```

Path Traversal:
```
http://127.0.0.1:5000/file?filename=./secret.txt
```
Brute Force Attack:
```
python bruteforce.py
```
