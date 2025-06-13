**Установка**
====================

#*Зависимости*
------------

Для установки нужны следующие компоненты:

* [php](http://www.php.net/) 

      1. версия >= 8.0

* [composer](https://getcomposer.org/) - менеджер зависимостей для [php](http://www.php.net/)

      1. Версия >= 2.0. Инструкцию по установке [composer](https://getcomposer.org/) можно посмотреть [здесь](https://getcomposer.org/download/)

         >
         > !!!!        
         > Смотрите официальный мануал по установке composer
         >

      2. Зависимости для [composer](https://getcomposer.org/) можно посмотреть [здесь](https://getcomposer.org/doc/00-intro.md#system-requirements)


* [Apache](https://httpd.apache.org)
    
     1. версия >= 2.2.4

     2. Модуль mod_rewrite

         >
         > Также вместо [Apache](https://httpd.apache.org) подойдут [nginx](https://nginx.org/ru) или [iis](https://ru.wikipedia.org/wiki/Internet_Information_Services)
         >



#*Установка*
------------


* Сгенерировать ssh-ключ. Так как репозиторий приватный, доступ к нему будет через ssh-ключи.

* Когда вы получите доступ выполнить для клонирования репозитория (**folder-name** замените директорией куда вы хотите клонировать репозиторий):

```
 git clone git@bitbucket.org:mkp_/mkp-portalOriginal.git folder-name
```

* Подтянуть зависимые пакеты через [composer](https://getcomposer.org/):

```
 composer install --no-dev
```

* Выполнить инициализацию приложения в __production__:

```
 php init
```

* В файле */common/config/main-local.php* заполнить пути, логин и пароль к базе BD и BDD.


* Прописать *DocumentRoot* поддоменов на директории *web* соответствующих модулей, например, */api/web* (какие есть модули можно посмотреть [здесь](https://bitbucket.org/mkp_/mkp-portalOriginal/wiki/Reference))