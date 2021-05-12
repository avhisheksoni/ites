# Files description #
# v.2.5.0 #



# laxyo.jar #

Server binary executable main file
DO NOT EXECUTE MANUALLY!!!



# Server manual control #


# ps.sh #

Show standart linux ps output only for laxyo server

Example:

sammy@gpsdev:~/laxyo$ ./ps.sh 
sammy     3450  0.2 12.0 2598684 122352 ?      Sl   Mar11   6:38 java -d64 -Djava.util.logging.config.file=./logging.properties -Xms64m -Xmx512m -Xss228k -jar laxyo.jar
sammy    18600  0.0  0.0  12916   924 pts/3    S+   19:46   0:00 grep java

Where:

3450 is server PID
0.2 is CPU usage, 0..100%
12.0 is RAM usage, 0..100%


# kill_ID.sh #

Kill server process by PID:

Example:

sammy@gpsdev:~/laxyo$ ./kill_ID.sh 3450

Where:

3450 is server PID

Server will restart in 10 sec.



# Server settings files #


# settings.json #

Server main settings file


# logging.properties #

Properties of java logger

Where:

.level=ALL
java.util.logging.FileHandler.level=ALL
java.util.logging.ConsoleHandler.level=ALL

is log verbosity. 
ALL is maximum verbosity. Less verbosity levels are:
FINEST, FINER, FINE, CONFIG, INFO, WARNING, SEVERE, OFF - no log at all




# Server starting scripts #


# run.sh #

Server run script, executed by loop.sh. 
DO NOT EXECUTE MANUALLY!!!

Here is Laxyo server start command:
 
java -d64 -Djava.util.logging.config.file="./logging.properties" -Xms64m -Xmx256m -Xss228k -jar laxyo.jar

-d64 - Start as 64-bit app
-Djava.util.logging.config.file="./logging.properties" - Loggings config
-Xms64m - Initial (start) heap size, depends on RAM size, on low RAM set to 64MB, on big RAM server 256MB is enough
-Xmx256m - Maximum heap size, depends on RAM size, set it to half of RAM size 
-Xss228k - Thread stack size, 228KB is optimal value


# loop.sh #

Server loop script, executed by cron. 
DO NOT EXECUTE MANUALLY!!!




# Server logs #


# nginx-error-log.sh #

Show nginx errors, need root rights.


# server-log.sh #

Show last server logs.


# output-0-???.log #

Server logs. output-0-0.log is newest log, output-0-1.log is older and so on.





# server REST commands #

Commands sended by curl to REST HTTP server module.


# version-get.sh #

Get server version.


# stats-get.sh #

Get server statistics, last trackers for 1 hour.


# settings-get.sh #

Get settings loaded to server.


# settings-PARAM-VALUE.sh #

Set server setting PARAM to value VALUE.
Deprecated. Instead change settings.json file and restart server.


# command-load_sett.sh #

Reload settings.
Deprecated. Instead simply restart server.


# command-reset.sh #

Restart server. Server will be restarted in 30-40 sec.


# command-start.sh #

Start receiving of trackers.


# command-stop.sh #

Stop receiving of trackers.




# Server security files #


# public.salt #

Generated random salt.
Do not change manually!


# security.json #

Generated security settings file.
Do not change manually!

Example:
{
  "GT300": true,
  "TK103": false,
  "AT06N": true,
  "IP": "12.34.56.78",
  "Date": "2019-03-31T07:04:44Z",
  "DaysToLive": 365,
  "Version": "1.0.0"
}

Description:
"GT300": true - Protocol GT300 is enabled
"TK103": false - Protocol TK103 is disabled
"IP": "12.34.56.78" - Server listen IP address
"Date": "2019-03-31T07:04:44Z" - Date of key generation
"DaysToLive": 365 - Days before key is expired
"Version": "1.0.0" - Security files version



# public.key #

Generated key for selected IP and tracker protocols. 

