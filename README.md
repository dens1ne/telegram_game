# Как перенести свою игру в Telegram?
Данный репозиторий содержит в себе подробный гайд по переносу своей игры в Telegram на примере GitHub Pages, для более удобного теста создается базовая структура сайта для GHPages (может использоваться не только там). Если пользователь хочет развернуть игру у себя на компьютере/сервере, необходимо иметь белый ip, для этого будет отдельный гайд.
В этом мануале реализован пример игры на Godot с помощью нашего инструмента и встроенного в Godot функционала.
## 1. Экспорт игры в HTML5 код
В разных движках есть для этого различные инструменты, в Godot уже реализована разработчиками функция (пока не реализована в Godot Mono (для .NET) >4).
1. Заходим в наш проект в Godot ![projects_menu](images/projects_menu.png "projects_menu")
2. Заходим во вкладку Project > Export ![export](images/export.png "export")
3. Add... > Web ![export_menu](images/export_menu.png "export_menu")
4. Если появляется ошибка, как здесь:![no_templates_error](images/no_templates_error.png "no_templates_error")
5. Нажимаем "Manage Export Templates":![manage_export_templates](images/manage_export_templates.png "manage_export_templates")
6. Открывается менеджер темплейтов для веба, нажимаем сразу "Download and Install" (примерно 1 ГБ) ![download_templates](images/download_templates.png "download_templates")
7. Нажимаем Close, возвращаемся в Project > Export и заходим в файловый менеджер  ![create_subdir](images/create_subdir.png "create_subdir")
8. Создаем папку под HTML5 код, файлу даем имя index.html! (это обязательно): ![create_subfolder](images/create_subfolder.png "Create subfolder") ![subfolder_name](images/subfolder_name.png "Subfolder") ![index](images/index.png "Index.html")

9. Save > Export Project... > Save ![exporting_project](images/exporting_project.png "Экспорт проекта")
10. Проверяем, что код был экспортирован: ![check_files](images/check_files.png "Проверка файлов")
11.  Также можно проверить, что код корректно запускается в браузере.
-  Устанавливаем Python (в терминале): 
	- На Windows: 
		```winget install python.python.3.13```
	- На Linux Debian/Ubuntu: 
		```sudo apt-get install python```
	- На Linux Fedora/Red Hat: 
		```sudo dnf install python```
	- На Linux Arch: 
		```sudo pacman -S python```
-  Заходим в папку с кодом HTML5 в терминале, и прописываем:
  	```python3 -m http.server```
-  В браузере в адресную строку вбиваем ```localhost:8000```
-  Проверяем работоспособность сервера:![testing](images/testing.png "Тестируем")
Теперь можно создавать репозиторий Github Pages.
## 2. Разворачиваем сервер с помощью Github Pages
12. Заходим в папку с вашим HTML5 кодом
13. Скачиваем скрипт под вашу систему (Linux/Windows) с официальной страницы релизов: https://github.com/dens1neBS/telegamesapi/releases и запускаем.
```bash
# Linux
curl -O https://github.com/dens1neBS/telegamesapi/releases/download/v0.1.2/upload_game.sh 
chmod +x upload_game.sh
./upload_game.sh

# Windows
curl -O https://github.com/dens1neBS/telegamesapi/releases/download/v0.1.2/upload_game.bat 
./upload_game.bat
```
1. Выполняем инструкции, что авторизоваться в GitHub. 
	 ![select_domain](images/authorization/authorizing.png)![select_https.png](images/authorization/select_https.png)![github_credentials](images/authorization/github_credentials.png)![login_with_a_web_browser.png](images/authorization/login_with_a_web_browser.png)
	Затем появившийся код вводим в окно браузера (откроется автоматически, если нажать Enter) ![one-time-code.png](images/authorization/one-time-code.png)![code_enter_field](images/authorization/code_enter_field.png)
	![configrm_authorization.png](images/authorization/configrm_authorization.png)

2. Выбираем "Push an exisiting repository to GitHub", затем нажимаем Enter до следующего пункта
	![push_repository.png](images/repository_creating/push_repository.png)
3. Когда будет запрашиваться название проекта ОБЯЗАТЕЛЬНО заполняем его по форме <ваш юзернейм в гитхабе>.github.io, иначе GitHub pages работать на вашем репозитории НЕ БУДЕТ!
	 ![repository_name.png](images/repository_creating/repository_name.png)
4. В области видимости выбираем "Public"
	![visibility](images/repository_creating/visibility.png)
5. Заходим на ваш репозиторий, чтобы проверить код: https://github.com/<ваш юзернейм>.github.io и сам сайт <ваш юзернейм>.github.io
6. Теперь заходим в телеграм в диалог с [@BotFather](https://t.me/BotFather)
	![base_message.png](images/telegram_dialogue/base_message.png)
7. Регистрируемся (если не были до данного момента) и вводим комманду /newbot
8. Создаем бота по инструкции
9. Затем вводим команду /newapp
10. Заполняем поля примерно вот так:
	![newwebapp.png](images/telegram_dialogue/newwebapp.png)
11. Вводим уникальный никнейм для приложения, и @BotFather выдает нам ссылку на игру!
	![final](images/telegram_dialogue/final.png)
12. Теперь у вас есть ссылка на вашу игру в рамках Telegram. Как её загрузить в вашего бота - смотрите в нашей документации к telegamesapi (https://github.com/dens1neBS/telegamesapi/wiki)

## 3. Cвязь с игрой с помощью telegamesapi
По началу может показаться, что в обратной связи нет смысла. Но если вам требуется реализовать удаленную связь с запущенной игрой, наш заготовленный код может вам помочь. В случаях когда нужно, например, получать информацию об активных игроках, продоставлен туториал для получения этих апдейтов с помощью telegamesapi в [официальном репозитории](https://github.com/dens1neBS/telegamesapi).
## 4. Пример реализации
В качестве примера реализована игра в [Telegram](https://t.me/testshittg_bot/html5gametest) и есть возможность посмотреть [исходный код](https://github.com/dens1ne/dens1ne.github.io) проекта.
