**Рекомендации**
===============



#*Https*
------------

Для большей надежности и безопасности рекомендуется для всех модулей использовать не [http-](https://ru.wikipedia.org/wiki/HTTP) , a [https-](https://ru.wikipedia.org/wiki/HTTPS) протокол.

>
> Бесплатный https-сертификат можно оформить с помощью [https://letsencrypt.org/](https://letsencrypt.org/). 
> Подробнее можно прочитать [здесь](https://letsencrypt.org/docs/) и [здесь](https://habrahabr.ru/post/270273/), а также [здесь](https://habrahabr.ru/post/304174/)
>


#*Cache*
------------

Рекомендуется для большего быстродействия использовать [Акселератор PHP](https://ru.wikipedia.org/wiki/%D0%90%D0%BA%D1%81%D0%B5%D0%BB%D0%B5%D1%80%D0%B0%D1%82%D0%BE%D1%80_PHP), к примеру, [Zend Opcache](http://php.net/manual/ru/book.opcache.php). ([Перевод настроек Zend Opcache](https://sabini.ch/cms/perevod-nastroek-zend-opcache.html))


#*Host header attack*
------------

[Описание](https://www.acunetix.com/vulnerabilities/web/host-header-attack)

Дополнительная информация [здесь](https://www.acunetix.com/blog/articles/automated-detection-of-host-header-attacks/) и [здесь](http://www.skeletonscribe.net/2013/05/practical-http-host-header-attacks.html)

Решение для [apache](http://httpd.apache.org/docs/trunk/vhosts/examples.html#defaultallports), [nginx](https://www.nginx.com/resources/wiki/start/topics/examples/server_blocks/)


#*Using secure connection over TLS*
------------

Yii provides features that rely on cookies and/or PHP sessions. These can be vulnerable in case your connection is
compromised. The risk is reduced if the app uses secure connection via TLS (often referred to as [SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security)).

Please refer to your webserver documentation for instructions on how to configure it. You may also check example configs
provided by the H5BP project:

- [Nginx](https://github.com/h5bp/server-configs-nginx)
- [Apache](https://github.com/h5bp/server-configs-apache).
- [IIS](https://github.com/h5bp/server-configs-iis).
- [Lighttpd](https://github.com/h5bp/server-configs-lighttpd).