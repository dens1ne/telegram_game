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
	-  Устанавливаем Python: 
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
	-  В браузере в адресную строку вбиваем ```loclhost:8000```
	-  Проверяем работоспособность сервера:![testing](images/testing.png "Тестируем")
Теперь можно создавать репозиторий Github Pages.
## 2. Разворачиваем сервер с помощью Github Pages
