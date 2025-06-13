**Обновление**
=================

#*Обновление*
------------

* Стянуть последние изменения с репозитория:

```
 git pull
```

* Подтянуть новые зависимые пакеты через [composer](https://getcomposer.org/):

```
 composer update --no-dev
```
* Выполнить инициализацию в **Production**:

```
 php init --env=Production
```

* Очистить cache базы:

```
php yii cache/flush-all
```