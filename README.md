# terminal_commands
Шпаргалка по командам терминала

Удаление:
- ```rm test.txt ``` - удалит файл с именем test.txt в текущей дирректории
- ```rm -r ./some_directory``` - удалит в текущей дирректории директорию some_directory со всеми ее поддирректториями и файлами, спрашивая подтвеждения об удалении для каждого вложенного ээлемента
- ```rm -rf ./some_directory``` - удалит в текущей дирректории директорию some_directory со всеми ее поддирректториями и файлами, не спрашивая подтвеждения об удалении для каждого вложенного ээлемента

Переименовать директорию:
- ```mv /home/user/oldname /home/user/newname``` - переименует директорию oldname в newname

Поиск файлов:

- ```find . -name "*.nate" -type f``` - поиск файлов по шаблону - найдет и выведет список всех файлов в имени кооторых присутствует ".meta" в текущем каталоге и его подкаталогах;
- ```find . -name "*.meta" -type f -delete``` - поиск файлов по шаблону - найдет и удалит все файлы в имени кооторых присутствует ".meta" в текущем каталоге и его подкаталогах;
- ```find DIR_NAME -type f | wc -l``` - кол-во файлов в директории;
- ```find ./ -name "*Zebr*" -type d``` - поиск директории в имени которой есть подстрока Zebr;


Перенаправление потока вывода в файл:
- ```command > output.txt``` - Стандартный поток вывода будет перенаправлен только в файл, он не будет виден в терминале. Если файл уже существует, он перезаписывается.

- ```command >> output.txt``` - Стандартный поток вывода будет перенаправлен только в файл, он не будет виден в терминале. Если файл уже существует, новые данные будут добавлены в конец файла.

- ```command 2> output.txt``` - Стандартный поток ошибок будет перенаправлен только в файл, он не будет виден в терминале. Если файл уже существует, он перезаписывается.

- ```command 2>> output.txt``` - Стандартный поток ошибок будет перенаправлен только в файл, он не будет виден в терминале. Если файл уже существует, новые данные будут добавлены в конец файла.

- ```command &> output.txt``` - И стандартный вывод, и стандартный поток ошибок будут перенаправлены только в файл, в терминале ничего не будет видно. Если файл уже существует, он перезаписывается.

- ```command &>> output.txt``` - И стандартный вывод, и стандартный поток ошибок будут перенаправлены только в файл, в терминале ничего не будет видно. Если файл уже существует, новые данные будут добавлены в конец файла.

- ```command | tee output.txt``` - Стандартный выходной поток будет скопирован в файл, он по-прежнему будет виден в терминале. Если файл уже существует, он перезаписывается.

- ```command | tee -a output.txt``` - Стандартный выходной поток будет скопирован в файл, он по-прежнему будет виден в терминале. Если файл уже существует, новые данные будут добавлены в конец файла.

- ``` ls -lR ./ | less``` - просмостр в программе less списка всех файлов, находящихся в текущей директории и всех ее поддиректориях;

(*)

Bash не имеет сокращенного синтаксиса, который позволяет передавать по конвейеру только StdErr второй команде, которая может понадобиться здесь в сочетании с teeagain для завершения таблицы. Если вам действительно нужно что-то подобное, пожалуйста, посмотрите "Как использовать stderr, а не stdout?" на Stack Overflow, чтобы узнать, как это можно сделать, например, путем замены потоков или использования подстановки процессов.

- ```command |& tee output.txt``` - И стандартный поток вывода, и стандартный поток ошибок будут скопированы в файл, оставаясь видимыми в терминале. Если файл уже существует, он перезаписывается.

- ```command |& tee -a output.txt``` - И стандартный поток вывода, и стандартные потоки ошибок будут скопированы в файл, оставаясь видимыми в терминале. Если файл уже существует, новые данные будут добавлены в конец файла.


Упаковка в архив:
- ```zip -r archive_name.zip folder_to_compress``` - пакует в архив archive_name.zip дирекорию folder_to_compress;
- ```zip -r archive_name.zip *``` - упакует в архив archive_name.zip вcе файлы в текущей директории;
- ```zip -r $archive_name.zip uncompressed *``` - упакует в архив archive_name.zip вcе файлы в текущей директории, без сжатия;

Рапаковка архивов:
- ```unzip archive_name.zip``` - распаковать архив archive_name;

git:
- ```git diff --no-renames --name-only --diff-filter=D``` - создание списка именудаленных файлов;
- ```git diff --no-renames --name-only --diff-filter=D -z | xargs -0 git checkout --``` - отмена удаленных файлов;
- ```git revert commit_id``` - отмена изменений внесенных комитом, идентификатор которого указан (commit_id);
- ```git log -p -- filename``` - просмотреть изменения по конкретному файлу в терминале;
