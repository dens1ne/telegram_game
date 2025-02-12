# Как перенести свою игру в Telegram?
Данный репозиторий содержит в себе подробный гайд по переносу своей игры в Telegram на примере GitHub Pages, для более удобного теста создается базовая структура сайта для GHPages (может использоваться не только там). Если пользователь хочет развернуть игру у себя на компьютере/сервере, необходимо иметь белый ip, для этого будет отдельный гайд.
В этом мануале реализован пример игры на Godot с помощью нашего инструмента и встроенного в Godot функционала.
## 1. Экспорт игры в HTML5 код
В разных движках есть для этого различные инструменты, в Godot уже реализована разработчиками функция (пока не реализована в Godot Mono (для .NET) >4).
1. Заходим в наш проект в Godot ![[projects_menu.png]]
2. Заходим во вкладку Project > Export ![[export.png]]
3. Add... > Web ![[export_menu.png]]
4. Если появляется ошибка, как здесь:![[no_templates_error.png]]
5. Нажимаем "Manage Export Templates":![[manage_export_templates.png]]
6. Открывается менеджер темплейтов для веба, нажимаем сразу "Download and Install" (примерно 1 ГБ) ![[download_templates.png]]
7. Нажимаем Close, возвращаемся в Project > Export и заходим в файловый менеджер ![[create_subdir.png]]
8. Создаем папку под HTML5 код, файлу даем имя index.html! (это обязательно): ![[create_subfolder.png]] ![[subfolder_name.png]] ![[index.png]]

9. Save > Export Project... > Save ![[exporting_project.png]]
10. Проверяем, что код был экспортирован: ![[check_files.png]]
11.  Также можно проверить, что код корректно запускается в браузере.
	1. Устанавливаем Python: 
		- На Windows: 
			```winget install python.python.3.13```
		- На Linux Debian/Ubuntu: 
			```sudo apt-get install python```
		- На Linux Fedora/Red Hat: 
			```sudo dnf install python```
		- На Linux Arch: 
			```sudo pacman -S python```
	2. Заходим в папку с кодом HTML5 в терминале, и прописываем:
		```python3 -m http.server```
	3. В браузере в адресную строку вбиваем ```loclhost:8000```
	4. Проверяем работоспособность сервера:![[testing.png]]
Теперь можно создавать репозиторий Github Pages.
## 2. Разворачиваем сервер с помощью Github Pages
