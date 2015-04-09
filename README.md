# 사전 작업
우분투 설치 [https://github.com/varteam/Install-Ubuntu14.04]

도커 설치 [https://github.com/varteam/Install-Docker-On-Ubuntu]

도쿠 설치 [https://github.com/varteam/Install-Dokku-on-ubuntu]

# Install-MongoDB-Plugin-For-Dokku
도쿠 플러그인 mongodb 설치 방법

    $ sudo git clone https://github.com/jeffutter/dokku-mongodb-plugin.git /var/lib/dokku/plugins/mongodb
    $ sudo dokku plugins-install
    
    $ dokku help
    mongodb:console                                 Launch an admin mongodb console
    mongodb:create <app> <database>                 Create a Mongo database and optional params for app
    mongodb:delete <app> <database>                 Delete specified Mongo database
    mongodb:dump <database> [-tar]                  Creates a binary export of the contents of database (-tar tarball dump)
    mongodb:link <app> <database>                   Set ENV variables for app if database exists
    mongodb:list                                    List all databases
    mongodb:logs                                    Show logs from MongoDB program
    mongodb:restore <database> <file-or dirname>    Restores the state of a database of a database exported with mongodb:dump
    mongodb:start                                   Start the MongoDB docker container if it isn't running
    mongodb:status                                  Shows status of MongoDB
    mongodb:stop                                    Stop the MongoDB docker container
