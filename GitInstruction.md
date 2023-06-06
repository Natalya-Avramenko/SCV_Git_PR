![Logo](logo.png)
## Работа с Git и GitHub

### 1. Проверка наличия установленного Git
В терминале выполнить команду `git --version`
Если Git установлен, появится сообщение с информацией о версии программы, иначе будет сообщение об ошибке.

### 2. Установка Git
Загружаем последнюю версию Git с сайта https://git-scm.com/downloads.
Устанавливаем с настройками по умолчанию.

### 3. Настройка Git
При первом использовании Git необходимо представиться. Для этого нужно ввести в терминале две команды:
```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
### 4. Инициализация репозитория
Для создания нового репозитория используется команда git init.
Данную команду выполняют только один раз для первоначальной настройки нового репозитория.
Выполнение команды приведет к созданию нового подкаталога .git в вашем рабочем каталоге. Кроме того, будет создана новая главная ветка.

### 5. Запись изменений в репозитории
* Команда Git status

Показывает текущее состояние гита, есть ли изменения, которые нужно закоммитить (сохранить).

* Команда git add

Добавляет содержимое рабочего каталога в индекс (staging area) для последующего коммита. Эта команда дается после добавления
файлов. Писать название целиком не обязательно: терминал дозаполнит данные автоматически.

* Команда git commit - зафиксировать или сохранить

По умолчанию git commit использует лишь этот индекс, так что вы можете использовать git add для сборки слепка вашего следующего коммита.
Команда git commit берёт все данные, добавленные в индекс с помощью git add, и сохраняет их слепок во внутренней базе данных, а затем сдвигает указатель текущей ветки на этот слепок.

* Команда git diff

Показывает разницу между текущим файлом и сохранённым.

### 6. Просмотр истории коммитов
Для просмотра истории коммитов используется команда *Git log* - выводит список всех коммитов.

У этой команды есть разные опции, самая используемая из них *--oneline*. Она показывает хеш в укороченном формате, ветку, в которой сделан коммит, а также текст коммита.

Чтобы использовать эту опцию (как и любую другую), нужно добавить её после команды: *Git log--oneline*.

### 7. Перемещение между сохранениями
Для переключениями между версиями используется команда __Git checkout__.

Для работы нужно указать не только интересующий вас коммит, но и вернуться в тот, где работаем, при помощи команды __Git checkout master__.

### 8. игнорирование файлов

Для того, чтобы исключить из отслеживания в репозитории определенные файлы и папки, необходимо создать там файл ***.gitignore*** и записать в него названия и шаблоны, соответствующие таким файлам или папкам.

### 9. Создание веток в Git
По умолчанию имя основной ветки в Git - *master*.
Создать ветку можно командой: 
```
git branch <имя новой ветки>
```
Список веток в репозитории можно посмотреть с помощью команды 
```
git branch
```
Текущая ветка будет отмечена звёздочкой: **\*master**

### 10. Слияние веток
Слияние используется в Git, чтобы собрать воедино разветвленную историю.
Слияние отдельных направлений разработки, созданных с помощью команды git branch, в единую ветку, выполняется с помощью команды:
```
git merge <имя ветки>
```
При этом необходимо обратить внимание на то, что команда выполняет слияние в текущую ветку. Поэтому команда git merge часто используется в сочетании с командой _git checkout_ (для выбора текущей ветки).

### 11. Разрешение конфликтов
При попытке объединить ветки, в которых изменена одна и та же часть того же файла, Git не сможет сделать выбор между версиями. В таком случае операция останавливается прямо перед созданием коммита слияния, чтобы пользователь вручную разрешил конфликты.

Преимущество слияния в Git заключается в том, что разрешение конфликтов при слиянии проходит по привычной схеме «редактирование — индексирование — коммит». При обнаружении конфликта выполните команду git status, чтобы увидеть, какие файлы необходимо исправить.

Если система Git столкнется с конфликтом во время слияния, она отредактирует содержимое затронутых файлов с помощью визуальных индикаторов, обозначающих обе стороны конфликтующего содержимого. Вот эти визуальные маркеры: <<<<<<<, ======= и >>>>>>>. Их полезно поискать в проекте во время слияния, чтобы определить, где необходимо урегулировать конфликты.

Обычно содержимое перед отметкой ======= относится к принимающей ветке, а все, что указано после нее, — к ветке, для которой выполняется слияние.

После обнаружения конфликтующих участков кода вы можете исправить их по своему усмотрению. Когда вы будете готовы завершить слияние, выполните команду git add для конфликтующего файла или файлов — так вы сообщите Git, что конфликт разрешен. Затем выполните обычную команду git commit, чтобы создать коммит слияния.

Преимущество слияния в Git заключается в том, что разрешение конфликтов при слиянии проходит по привычной схеме «редактирование — индексирование — коммит». При обнаружении конфликта выполните команду git status, чтобы увидеть, какие файлы необходимо исправить.

### 12. Удаление веток
Чтобы удалить локальную ветку в Git нужно выполнить команду:
```
git branch -d <название ветки>
```
Обратите внимание на то, что ветка, которую вы удаляете, не должна быть вашей текущей веткой, в которой вы работаете, иначе отобразится ошибка вида:

**error: Cannot delete branch <название ветки> checked out at ’/path/to**

Поэтому, если вам нужно удалить текущую ветку, то сначала нужно переключиться на какую-либо другую ветку, а только потом выполнять удаление.

Если вдруг возникает ошибка: 
**The branch <название ветки> is not fully merged. If you are sure you want to delete it**
 и вы по прежнему хотите удалить ветку, то для принудительного удаления ветки можно воспользоваться опцией -D:
 ```
 git branch -D <название ветки>
 ```
 