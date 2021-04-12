## Оптимизированная сборка Gulp для верски

# Запуск

Выгружаем репозиторий

    git clone https://github.com/Fargrab/gulp-template.git

 Переходим в директорию

    cd gulp-template

    
 Устанавливаем нужные нам компоненты

    npm install
 Если есть шрифты в формате "otf"
   
    gulp otf2ttf
Запускаем Gulp

    gulp
Если работаете с SVG. То все инструкции в описании п.6
    
   
## Описание сборки.

1. HTML

Подключен шаблонизатор Html файлов. В файле index.htm закомментированы пример подключения Html компонентов. 
!!!ВНИМАНИЕ!!! Для того чтобы не компилировались компоненты html в готовый build название должно начинаться с "_". Пример: "_header.html".
Забирает все файлы .html не начинающиеся с символа "_" во всех вложенных папках в исходной "#src".

2. CSS (Sass)

Настроена автоматическая компиляция сразу в 2ух форматах. 1-ый минимизированный для оптимизации сайтов. 2-ой развернутый для удобства дальнейшей поддержки. 
Так же подключен плагин для группировки медиа запросов.
Все переменные записываем в файл variables.scss
Забирает один файл "style.scss" из "#src/scss", все остальные стили подключаем к нему.

3. Шрифты.

Настроен автоматический конвектор шрифтов из формата "ttf" в форматы "woff", "woff2". 
Добавлен mixin шрифтов, который автоматически добавляет шрифты в файлы стилей. Нужно только  после запуска сборщика в файле "#src/scss/fonts.scss"  редактировать имя семейства потому что он берет имя названия файла, и жирность, по умолчанию ставит значение normal(400).
Если в исходниках есть шрифты формата "otf", то перед запуском сборщика запустите функцию "gulp otf2ttf". Функция автоматически форматирует файлы с форматом "otf" в формат "ttf".
Все исходники закидываем в папку "#src/fonts"

4. JS файлы

Настроена автоматическая компиляция сразу в 2ух форматах. 1-ый минимизированный для оптимизации сайтов. 2-ой развернутый для удобства дальнейшей поддержки. 
Забирает один файл "scripts.js" из "#src/js", все остальные скрипты подключаем к нему.

5. Изображения

Добавлен автоматический конвектор в webp.
В папку результата с изображениями сохраняются два файла в формате "webp" и с оригинальным разрешением.(Сжатые на 70%)
При подключении изображений в Html разметку указывайте исходный формат, т.к. добавлена функция проверки поддержки формата webp браузером, автоматически подключающая один из форматов в зависимости от поддержки браузером. 
Все исходники закидываем в папку "#src/img". Забирает все файлы из всех подпапок в форматах .{jpg,png,gif,svg,ico,webp}

6. SVG спрайты

Функция запускается отдельно и только после запуска сборщика. (За нечастым их использованием)
!!!ВНИМАНИЕ!!!! Если перезапустить сборщик спрайты удаляются автоматически. Их нужно будет снова собирать. (Я их немного редактирую и на время работы над проектом делаю копию
в корневой папке проекта).
Запустить командой в отдельном терминале. 

    gulp svgSprite
Все исходники закидываем в папку "#src/iconsprite". Собранный спрайт находится "../img/stack/svg"

7. Автоматическое удаление старой папки с результатом компиляции и создание новой.

8. Автоматический запуск в браузере и автоматическое обновление страницы при сохранении файла.

9. Папка с результатом автоматически именуется названием родительской.

