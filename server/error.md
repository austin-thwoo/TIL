OutOfMemory : heap
- 힙사이즈 메모리 부족에 대한 에러
- 올려놓은 파일을 프론트에서 다시 받을때 에러가 생겼다
  
  해결:
  자르파일을 실행시키면서 heap사이즈 설정을 해주었다.
```java
  #!/bin/sh
SERVICE_NAME=poc_be_spring_v1_server
PATH_TO_JAR=./poc_be_spring-0.0.1-SNAPSHOT.jar
PID_PATH_NAME=./poc_be_spring_v1_server.pid
case $1 in
    start)
        echo "Starting $SERVICE_NAME ..."
        if [ ! -f $PID_PATH_NAME ]; then
            nohup java -jar -Xms128m -Xms1024m $JAVA_OPT $PATH_TO_JAR & /*여기에 -Xms128m -Xms1024m 을 추가해주었다. -> heap사이즈 영역 늘리기*/
                        echo $! > $PID_PATH_NAME
            echo "$SERVICE_NAME started ..."
        else
            echo "$SERVICE_NAME is already running ..."
        fi
    ;;
    stop)
        if [ -f $PID_PATH_NAME ]; then
            PID=$(cat $PID_PATH_NAME);
            echo "$SERVICE_NAME stoping ..."
            kill -15 $PID;
            echo "$SERVICE_NAME stopped ..."
            rm $PID_PATH_NAME
        else
            echo "$SERVICE_NAME is not running ..."
        fi
    ;;
    restart)
        if [ -f $PID_PATH_NAME ]; then
            PID=$(cat $PID_PATH_NAME);
            echo "$SERVICE_NAME stopping ...";
            kill -15 $PID;
            echo "$SERVICE_NAME stopped ...";

```