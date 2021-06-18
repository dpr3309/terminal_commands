# terminal_commands
Шпаргалка по командам терминала

Удаление:
```rm test.txt ``` - удалит файл с именем test.txt в текущей дирректории
```rm -r ./some_directory``` - удалит в текущей дирректории директорию some_directory со всеми ее поддирректториями и файлами, спрашивая подтвеждения об удалении для каждого вложенного ээлемента
```rm -rf ./some_directory``` - удалит в текущей дирректории директорию some_directory со всеми ее поддирректториями и файлами, не спрашивая подтвеждения об удалении для каждого вложенного ээлемента

Поиск файлов:

- ```find . -name "*.nate" -type f``` - поиск файлов по шаблону - найдет и выведет список всех файлов в имени кооторых присутствует ".meta" в текущем каталоге и его подкаталогах;
- ```find . -name "*.meta" -type f -delete``` - поиск файлов по шаблону - найдет и удалит все файлы в имени кооторых присутствует ".meta" в текущем каталоге и его подкаталогах;
