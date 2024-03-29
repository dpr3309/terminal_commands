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

grep
- ```grep -i -R 'logEvent' .``` - !!!!  последний символ точка - . !!!!!  поиск строк содержащих logEvent во всех файлах текущей директории

diff
- ```diff -y -W 70 alpha1 alpha2``` - сравнение двух файлов в терминале

git:
- ```git diff --no-renames --name-only --diff-filter=D``` - создание списка именудаленных файлов;
- ```git diff --no-renames --name-only --diff-filter=D -z | xargs -0 git checkout --``` - отмена удаленных файлов;
- ```git revert commit_id``` - отмена изменений внесенных комитом, идентификатор которого указан (commit_id);
- ```git log -p -- filename``` - просмотреть изменения по конкретному файлу в терминале;
- ```git reset HEAD~``` - отменить последний локальный коммит, изменения останутся.
- ```git filter-branch --index-filter "git rm --cached --ignore-unmatch path/to/file" --prune-empty HEAD``` - В случае, если вам необходимо полностью удалить файл из истории git - вам потребуется выполнить совсем не простую команду. другими словами - пройдет по истории текущей ветки и затрет во всех коммитах файл/директорию, и удалит из интекса. ВНИМАНИЕ! изменится sha комитов, и может потребоваться форс пуш, если ветка в удаленном репозитории уже есть
- ```git status -v``` - показать изменения которые застейджены (после применения команды git add к файлу, изменения из этого файла попадают в Changes to be committed) но еще не закомичены;
- ```git checkout [commit ID] -- path/to/file``` - revert single file from commit;
- ```git rm file1.txt```
  ```git commit -m "remove file1.txt"``` - удаление файла из репозитория;

other:
- ```apktool d /Users/mac02/Projects/Builds/dev2.apk``` - распакует в директорию dev2 в текущей диркектории apk-шку, и в ней можно будет глянуть ресурсы и манифест
- ```/Applications/Unity/Hub/Editor/2021.1.10f1/Unity.app/Contents/MacOS/Unity -batchmode -logfile /dev/stdout -quit -customBuildName iOS -projectPath . -buildTarget iOS -customBuildTarget iOS -customBuildPath /github/workspace/build/iOS/iOS -executeMethod ContinuousIntegration.BuildIos -buildVersion none -androidVersionCode 0 -androidKeystoreName -androidKeystorePass -androidKeyaliasName -androidKeyaliasPass -androidTargetSdkVersion --skazbukaProd true -quitTimeout 6000``` - запуск сборки билда сказбуки из терминала - аля ci/cd
- ```sysctl -n hw.ncpu``` - узнать кол-во ЦПУ на маке
- ```cat /proc/cpuinfo``` - узнать кол-во ЦПУ на linux
- ```uname -a``` - получить информацию о аппаратной платформе. (выдаст длинную строку, ближе к концу которой можно найти обозначение аппаратной архитектуры: i386, i586, i686, x86 - 32-битный проц; x86_64, amd64,... - 64-битные процы)
- ```pwd``` - текущий путь
