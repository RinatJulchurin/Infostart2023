# Опыт использования оптимизированного механизма реструктуризации (v2) на базе размером 36 терабайт.
## Дополнительные материалы
### Обработка для получения разницы индексов по данным 1С и СУБД
Обработка работает на сервере 1С под Windows используя COM-объект ADODB.
Обработка проверяет, что база в которой запущена обработка и база подключенная через ADODB одна и та же.
По умолчанию обработка подключается в попытке к MS-SQL, а при ошибке подключается к PostgreSQL.
В примере на скриншоте удален типовой индекс, а вместо типового добавлен вручную индекс с полем include.
![Обработка](./img/Обработка.png)

### Файл настроек технологического журнала для реструктуризации v2
![logcfg.xml](./logcfg.xml)

Пример логов
```
34:34.008000-0,SYSTEM,0,level=DEBUG,component=dmf,class=com._1c.dmf.internal.sqlframework.SqlConnection,line=,file=,threadId=1,message='Query started. Text query: UPDATE __alias1 WITH(TABLOCK) SET _Fld73_TYPE_NO = CASE WHEN ((__alias1._Fld73_TYPE = 0x08) AND (__alias1._Fld73_RTRef = 0x00000047)) THEN 0x01 ELSE __alias1._Fld73_TYPE END, _Fld73_RRRef_NO = CASE WHEN ((__alias1._Fld73_TYPE = 0x08) AND (__alias1._Fld73_RTRef = 0x00000047)) THEN 0x00000000000000000000000000000000 ELSE __alias1._Fld73_RRRef END, _Fld73_RTRef_NO = CASE WHEN ((__alias1._Fld73_TYPE = 0x08) AND (__alias1._Fld73_RTRef = 0x00000047)) THEN 0x00000000 ELSE __alias1._Fld73_RTRef END FROM _InfoRg72 AS __alias1'
34:34.015000-0,SYSTEM,0,level=DEBUG,component=dmf,class=com._1c.dmf.internal.sqlframework.SqlConnection,line=,file=,threadId=1,message='Query was completed in 7 millis. Text query: UPDATE __alias1 WITH(TABLOCK) SET _Fld73_TYPE_NO = CASE WHEN ((__alias1._Fld73_TYPE = 0x08) AND (__alias1._Fld73_RTRef = 0x00000047)) THEN 0x01 ELSE __alias1._Fld73_TYPE END, _Fld73_RRRef_NO = CASE WHEN ((__alias1._Fld73_TYPE = 0x08) AND (__alias1._Fld73_RTRef = 0x00000047)) THEN 0x00000000000000000000000000000000 ELSE __alias1._Fld73_RRRef END, _Fld73_RTRef_NO = CASE WHEN ((__alias1._Fld73_TYPE = 0x08) AND (__alias1._Fld73_RTRef = 0x00000047)) THEN 0x00000000 ELSE __alias1._Fld73_RTRef END FROM _InfoRg72 AS __alias1'
```
### Ошибки при реструктуризации v2
