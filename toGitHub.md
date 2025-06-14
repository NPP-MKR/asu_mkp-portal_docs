# Инструкция: переход на новый GitHub-репозиторий

## 1. Перейдите в папку с проектом

Откройте терминал и выполните:
```bash
cd путь_до_вашего_проекта/mkp-portaloriginal
```

- **Linux**: обычный пользователь (не sudo)
- **Windows**: CMD, PowerShell или Git Bash — запуск **не от администратора**, если нет особой необходимости

---

## 2. Сгенерируйте SSH-ключ

**Рекомендации:**

- Лучше всегда сохранять ключ в папке `~/.ssh`
- Не используйте `sudo` при создании `.ssh/config`, иначе будут проблемы с правами
- Проверьте права доступа (Linux):
  ```bash
  chmod 700 ~/.ssh
  chmod 600 ~/.ssh/id_mkp
  ```

**Создание ключа:**
```bash
ssh-keygen -t ed25519 -C "Название вашего ВУЗа"
```

**Примеры путей для сохранения:**

- **Linux**: `/home/пользователь/.ssh/id_mkp`
- **Windows**: `C:\Users\ваш_логин\.ssh\id_mkp`

**Пример с указанием пути:**
```bash
# Linux
ssh-keygen -t ed25519 -C "id_mkp" -f ~/.ssh/id_mkp

# Windows
ssh-keygen -t ed25519 -C "id_mkp" -f C:\Users\ваше_имя\.ssh\id_mkp
```

---

## 3. Настройка файла `~/.ssh/config`

### Linux
```bash
echo -e "Host github-mkp\n  HostName github.com\n  User git\n  IdentityFile ~/.ssh/id_mkp" >> ~/.ssh/config
chmod 600 ~/.ssh/config
```

### Windows (Git Bash)
```bash
echo -e "Host github-mkp\n  HostName github.com\n  User git\n  IdentityFile C:/Users/ваш_логин/.ssh/id_mkp" >> ~/.ssh/config
```

### Windows (PowerShell)
```powershell
Add-Content -Path "$env:USERPROFILE\.ssh\config" -Value "Host github-mkp`n  HostName github.com`n  User git`n  IdentityFile C:/Users/$env:USERNAME/.ssh/id_mkp"
```

### Windows (Командная строка)
```cmd
echo Host github-mkp>> %USERPROFILE%\.ssh\config
echo   HostName github.com>> %USERPROFILE%\.ssh\config
echo   User git>> %USERPROFILE%\.ssh\config
echo   IdentityFile C:/Users/%USERNAME%/.ssh/id_mkp>> %USERPROFILE%\.ssh\config
```

---

## 4. Отправка публичного ключа

Найдите файл `id_mkp.pub` и отправьте его на почту:

```
info@mkr.org.ua
```

В письме обязательно укажите название ВУЗа.

---

## 5. Обновление репозитория

Выполните в каталоге проекта:
```bash
git remote set-url origin git@github-mkp:NPP-MKR/mkp-portaloriginal.git
```

Проверьте доступ:
```bash
ssh -T git@github-mkp
```

Если появляется вопрос:
```
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Введите `yes` и нажмите Enter.

Теперь `git pull` будет работать из GitHub с новым ключом.