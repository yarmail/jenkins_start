<a href="/README.md">вернуться к оглавлению</a>

<b>Установка и запуск Jenkins</b> <br><br>

Находим и скачиваем версию Jenkins<br>
`jenkins.io/download/` <br>
в виде .war файла. В моем случае последняя стбильная версия 2.401.3 LTS мне не подошла, <br>
не устанавливались плагины (возможно это связано с версией JDK) <br>
и я начал откатываться по версиям назад, (можно посмотреть версии на этой странице) <br>
`get.jenkins.io/war-stable/` <br>
Остановился на версии 2.387.1 <br>
`get.jenkins.io/war-stable/2.387.1/`<br><br> 

Копируем этот файл в папку <br>
`c:\tools\jenkins` <br>
Открываем терминал в этой папке и проверяем есть ли возможность <br>
запускать java файлы на этом компьютере <br>

<pre> 
C:\Tools\jenkins>java -version

java version "17.0.2" 2022-01-18 LTS
Java(TM) SE Runtime Environment (build 17.0.2+8-LTS-86)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.2+8-LTS-86, mixed mode, sharing)
</pre>

После этого запускаем Jenkins <br>
`C:\Tools\jenkins>java -jar jenkins.war` <br>
Обычно Jenkins по умолчанию запускается на порте 8080. <br>
Если этим портом уже пользуется какой-то другой сервис, можно указать при запуске <br>
Jenkins другой порт, воспользовавшись командой такого вида:<br>
`java -jar jenkins.war --httpPort=8081`<br>
Если все запустилось нормально, вы должны увидеть сообщения примерно такого вида:<br>

<details>
<summary>Лог запуска Jenkins</summary>
<pre>
C:\Tools\jenkins>java -jar jenkins.war
Running from: C:\Tools\jenkins\jenkins.war
webroot: C:\Users\01-2017\.jenkins\war
2023-08-21 09:12:56.943+0000 [id=1]     INFO    winstone.Logger#logInternal: Beginning extraction from war file
2023-08-21 09:13:01.193+0000 [id=1]     WARNING o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
...
2023-08-21 09:13:07.406+0000 [id=61]    INFO    hudson.util.Retrier#start: Attempt #1 to do the action check updates ser
ver
2023-08-21 09:13:08.346+0000 [id=44]    INFO    jenkins.install.SetupWizard#init:

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

223dac81333d4cd3830d80b402d78126

This may also be found at: C:\Users\01-2017\.jenkins\secrets\initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

2023-08-21 09:13:33.158+0000 [id=44]    INFO    jenkins.InitReactorRunner$1#onAttained: Completed initialization
2023-08-21 09:13:33.798+0000 [id=61]    INFO    h.m.DownloadService$Downloadable#load: Obtained the updated data file fo
r hudson.tasks.Maven.MavenInstaller
2023-08-21 09:13:38.127+0000 [id=61]    INFO    hudson.util.Retrier#start: Performed the action check updates server suc
cessfully at the attempt #1
2023-08-21 09:13:38.237+0000 [id=27]    INFO    hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running
</pre>
</details>

Примечание 1: как я понимаю, если у вас не установлен Maven, будут ошибки <br>
Примечание 2: для дальнейшей работы нам понадобится вот эта строка лога: <br>
`223dac81333d4cd3830d80b402d78126` (у вас будет своя) как временный пароль для входа  <br>
Примечание 3: Не всегда все плагины устанавливаются нормально и сразу, <br> 
несколько раз пришлось нажимать кнопку Retry<br>
Примечание 4. Если требуется переустановка другой версии (или удаление): <br> 
~ останавливаем файл процесс в CMD - CTRL+C<br>
~ Удаляем установленную конфигурацию jenkins, которая по умолчанию должна <br> 
находится по адресу типа: <br>
`C:\Users\"User_name"\.jenkins` <br>
~ начинаем процесс заново





