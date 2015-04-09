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


# 몽고 디비 설정 방법

     //몽고 db 컨테이너 생성
     $ dokku mongodb:start
     
     //db 와 유저 생성
     $ dokku mongodb:create mean mean
     Successfully added user: {
        	"user" : "mean",
        	"roles" : [
        		{
        			"role" : "dbOwner",
        			"db" : "mean-production"
        		}
        	]
        }

     //디비와 유저 연결(환경변수 값 생성)
     $ dokku mongodb:link mean mean
     -----> mean linked to jeffutter/mongodb:latest container

     //환경 설정값 보기
     $ dokku config mean
     =====> mean config vars
        DOKKU_DOCKERFILE_PORT: 3000
        MONGODB_DATABASE:      "mean-production"
        MONGODB_HOST:          "172.17.0.23"
        MONGODB_PORT:          "27017"
        MONGODB_USERNAME:      "mean"
        MONGODB_PASSWORD:      "disxcG10SC9kUkpoMnRKN2hPQ0lEM29LdkY2WmhDOXpXcURiU3ZnQWZIaz0K"
        MONGO_URL:             "mongodb://mean:disxcG10SC9kUkpoMnRKN2hPQ0lEM29LdkY2WmhDOXpXcURiU3ZnQWZIaz0K@172.17.0.23:27017/mean-production"
        MONGO_URI:             "mongodb://mean:disxcG10SC9kUkpoMnRKN2hPQ0lEM29LdkY2WmhDOXpXcURiU3ZnQWZIaz0K@172.17.0.23:27017/mean-production"

# 이후 작업
Node 에서 환경 설정값으로 위의 환경 변수를 활용하여 mongodb 연결
