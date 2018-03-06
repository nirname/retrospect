# Zabbix

В разделе Configuration есть такая штука как Discovery, через неё настраивается автоматическое подключение хостов.

Там же в Configuration есть поле Action, Event source Auto registration

Там создаем действие

В поле Conditions создаем условия добавления хоста. Я например чтобы все хосты добавлялись написал Host name not like lalala и для хостов за прокси сервером Proxy = proxy.example.com

в поле Operations делаю

```bash
Add host
Add to host groups: Discovered hosts
Link to templates: base_linux_tmpl
```

сохранаю и все хосты у которых сервером стоит наш сервер автоматически добавляются, добавляются в группу Discovered hosts и им добавляется темплейт base_linux_tmpl


## Template

Configuration -> Templates

Набор планов по которым идут проверки, составляются отчеты, гафики и срабатывают натификации.
Их можно создавать, экспортировать / импортировать

Всё это можно делать и для отдельного хоста, но темплейт хорош тем что туда можно добавлять и убирать много хостов

Основной элемент - Items. Там задается что проверяется и как, а в Triggers задается условия срабатывания оповещений.

Например темплейт Template App Zabbix Agent в Items есть Agent ping который выполняет запрос к агенту agent.ping и получает в ответ значение 0 или 1.
В Triggers  же для него есть срабатывание с именем Zabbix agent on {HOST.NAME} is unreachable for 5 minutes задается условие

    {Template App Zabbix Agent:agent.ping.nodata(5m)}=1

по которому если в течение 5 минут от соответсвующго item приходит значение 1, то срабатывает нотификация.

Также, помимо Items Triggers есть Web scenarios, где можно настраивать хождение по страничкам како-то сайта и Discovery rules.
Немного сложнее чем Items Triggers, там сперва динамически получаются какие-то параметры, а потом по ним осуществляются проверки.

Напрмер если в Items мы задаем проверку конкретного диска (пишем его имя), в Discovery rules мы сперва получаем актуальный список названий дисков и потом уже осуществляем проверку по ним