##  Добро пожаловать в руководство для выбешенного студента Я.Практикума

Если Вы упорно не могли починить картинки в течение нескольких дней, то добро пожаловать!
Если места на вашей виртуальной машине не хватало - тоже welcome!

Вот оно, рабочее: https://k92.tech

### Как была решена проблема с отсутствием места на ВМ:
На самом деле очень просто!
1. Идёте в ближайший магазин
2. Покупаете себе Orange Pi
3. Накатываете armbian
4. Ребилдите все образы под linux/arm64
5. Перезаливаете на докерхаб

Не забываем чутка поменять main.yml в деплое,
проще вместо SSH_KEY и PASSPHRASE использовать просто PASSWORD.
Это отняло около дня (только оранж пай у меня уже был).

Да, есть вариант и с командами, которые освободят чуть-чуть места на ВМ Яндекса, но мы выбираем путь, где всё своё.

Потому что айти-гигант уже в который раз выступает в роли примера фразы "колосс на глиняных ногах".

### Как была решена проблема с картинками:
Ещё проще, чем покупка Orange Pi!

1. Упорно два дня пытаетесь решить проблему самостоятельно на локальной машине, всё получается
2. Заливаете на ВМ или OPi и убеждаетесь, что картинки опять не работают
3. Следующие два дня ищете помощь у сокурсников и старших товарищей, которые разбираются в докере
4. Понимаете, что проблема была не в докере, а в настройках nginx
5. Пытаетесь ещё денёк понасиловать nginx.conf
6. Он насилует Вас
7. Заходите на Гитхаб и в поиске находите проект другого студента
8. Копируете его настройки
9. Опять ребилдите образ kittygram_gateway
10. Во внешнем nginx ставите следующие настройки (БОЛЬШЕ НИКАКИХ РУТОВ НЕ НУЖНО! ТОЛЬКО ' / '!):
```
server {

    server_name <ваш-домен>;

    location / {
        proxy_set_header Host &http_host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_pass http://127.0.0.1:9000;
    }

}
```
11. Идёте радоваться/плакать/спать/истерить/
12. Сдаёте на ревью, чтобы ревьюер отправил писать обычный README.md
