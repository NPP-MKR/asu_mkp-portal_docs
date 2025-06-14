1) Откройте терминал и перейдите в проект
Выполните:  cd путь_до_вашего_проекта/mkp-portaloriginal
Linux: обычный пользователь (не sudo)
Windows: CMD, PowerShell или Git Bash — запуск не от администратора, если нет особой необходимости

2) Сгенерируйте SSH-ключ:
Рекомендации: 
Лучше всегда создавать ключ в папке ~/.ssh 
Не используйте sudo при создании .ssh/config, иначе будет ошибка прав
Убедитесь, что права доступа к файлам ключей корректны (для Linux):
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_mkp

Выполните команду: ssh-keygen -t ed25519 -C "Название вашего ВУЗа"
Спросит путь сохранения, примеры путей для сохранения ключей:
Linux: /home/пользователь/.ssh/id_mkp
Windows: C:\Users\ваш_логин\.ssh\id_mkp
Можно сгенерировать ключ с заранее заданным путём сохранения, но в идеале использовать папку по умолчанию:
Linux: ssh-keygen -t ed25519 -C "id_mkp" -f ~/.ssh/id_mkp
Windows: ssh-keygen -t ed25519 -C "id_mkp" -f C:\Users\ваше_имя\.ssh\id_mkp

3) Настройка файла ~/.ssh/config
Linux (в терминале):
echo -e "Host github-mkp\n  HostName github.com\n  User git\n  IdentityFile ~/.ssh/id_mkp" >> ~/.ssh/config
chmod 600 ~/.ssh/config

Windows (в Git Bash):
echo -e "Host github-mkp\n  HostName github.com\n  User git\n  IdentityFile C:/Users/ваш_логин/.ssh/id_mkp" >> ~/.ssh/config

Windows (в PowerShell):
Add-Content -Path "$env:USERPROFILE\.ssh\config" -Value "Host github-mkp`n  HostName github.com`n  User git`n  IdentityFile C:/Users/$env:USERNAME/.ssh/id_mkp"

Windows (Командная строка, можно выполнять по очереди каждую строку):
echo Host github-mkp>> %USERPROFILE%\.ssh\config
echo   HostName github.com>> %USERPROFILE%\.ssh\config
echo   User git>> %USERPROFILE%\.ssh\config
echo   IdentityFile C:/Users/%USERNAME%/.ssh/id_mkp>> %USERPROFILE%\.ssh\config

4) Отправьте публичный ключ. Найдите созданный файл id_mkp.pub (публичный ключ) и отправьте его на: info@mkr.org.ua
В письме укажите, от какого ВУЗа ключ.

5) Перейдите в папку с порталом и выполните:
git remote set-url origin git@github-mkp:NPP-MKR/mkp-portaloriginal.git

Теперь git pull будет работать из GitHub с новым ключом. После того как мы добавим ваш ключ, вы можете дополнительно проверить доступ:
ssh -T git@github-mkp
Первый раз может спросить: Are you sure you want to continue connecting (yes/no/[fingerprint])?
Введите: yes и нажмите Enter.
