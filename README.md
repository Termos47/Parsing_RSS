# Docker-образ для сервиса Fivefilters Full-Text RSS

## Этот репозиторий основан на репозитории https://github.com/heussd/fivefilters-full-text-rss-docker.git, изменения не затронут основную работу сайта а лишь конфигурационные файлы и перевод на русский язык.

![Docker build and push](https://github.com/heussd/fivefilters-full-text-rss-docker/workflows/Docker%20build%20and%20push/badge.svg)
![Number of Image Pulls](https://img.shields.io/docker/pulls/heussd/fivefilters-full-text-rss)
![Image size](https://img.shields.io/docker/image-size/heussd/fivefilters-full-text-rss/latest)


Это контейнерная версия [fivefilters full-text-rss](https://www.fivefilters.org/full-text-rss/), который извлекает полный текст отдельных статей или полные полнотекстовые RSS-каналы.

Не связан с [fivefilters.org](http://fivefilters.org/). Файл Dockerfile лицензирован в соответствии с [условиями MIT] (ЛИЦЕНЗИЯ).

## Руководство пользователя

-   Use the following [compose.yml](compose.yml)
-   Используйте следующий файл (compose.yml)

```yaml
services:
    fullfeedrss:
        image: 'heussd/fivefilters-full-text-rss:latest'
        environment:
            # Leave empty to disable admin section
            - FTR_ADMIN_PASSWORD=1234 #CHANGE PASSWORD
        volumes:
            - 'rss-cache:/var/www/html/cache/rss'
        ports:
            - '80:80'
volumes:
    rss-cache:
```

-   Запустите контейнер `docker-compose up`
-   Проверьте [http://localhost:80](http://localhost:80) для интегрированного веб-интерфейса

![](webui.png)

-   Interesting endpoints (see tab [Request & Response](http://localhost/#request)):
    -   Article extraction: `http://localhost/extract.php?url=[url]`
    -   Feed conversion: `http://localhost/makefulltextfeed.php?url=[url]`
-   See [calls.http](calls.http) for example calls
