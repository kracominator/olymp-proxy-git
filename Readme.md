Представляет собой http прокси сайта olymptrade.com и служит для регистрации трейдеров из запрещенных гео. 
Так же присутствует поддержка регистрации трейдеров с лендинга.  

#### Доступные сборки
[Linux/x86_64](olymp-proxy_linux_386)  
[Linux/amd_64](olymp-proxy_linux_amd64)

#### Установка
1. Регистрируем виртуальный хостинг (например на digitalocean.com https://m.do.co/c/855165db7c59) 
 на **Linux/x86_64 или Linux/amd_64**, например **Ubuntu 16.04.5 x64**.   
2. Скачиваем нужный бинарник и загружаем его на сервер, даем права на исполнение файла  
`chmod 0744 olymp-proxy-{version}`
3. Для работы с прокси, положите рядом с исполняемым файлом текстовый файл под названием _proxy_ со списком прокси, каждый адрес с новой строки, например  
http://217.21.60.160:42452  
http://86.57.171.111:57612  
4. Запускаем сервер  
`./olymp-proxy-{version} -id AFFILIATE_ID`  
где AFFILIATE_ID - ваш партнерский id
5. Сервер будет слушать 80 порт. Чтобы изменить порт, запустите сервер с параментор -port  
`./olymp-proxy-{version} -id AFFILIATE_ID -port PORT`  
**Внимание!** На сервере не должен быть запущен ни один прочий http сервер (apache, nginx и тд), работающий по тому же порту (по умолчанию 80). В противном случае, этот сервер будет перехватывать запросы и регистрация не сработает.

Сервер будет проксировать страницу olymptrade.com. При регистрации пользователи будут перенаправляться на olymptrade.com.
При этом им надо будет заново авторизоваться.

#### Остановка сервера
Для штатной остановки сервера, воспользуйтесть параметром _-s quit_  
`./olymp-proxy-{version} -s quit`  

#### Регистрация с лендинга
Вы также можете создать свой лендинг для привлечения клиентов.
Пример легдинга находится в папке [/landing](/landing). Скопируйте ее в папку с бинарником.   
Сама ссылка будет выглядететь так: _yourhost/landing_.  
Вы можете модифицировать лендинг как хотите. Главное оставить блок с пикселем, для того, чтобы клиент успешно привязался к партнеру. Так же требуется сохранить логику отправки формы на _/user/registration_ и названия параметров.



