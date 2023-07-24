## <span style = "color:purple"> [1].docker-compose </span>

Docker Compose는 Docker 컨테이너 기반 애플리케이션을 정의하고 실행하기 위한 도구로서, YAML 파일 형식을 사용하여 여러 개의 도커 컨테이너를 하나의 애플리케이션 스택으로 정의하고 구성하는 도구</br>
이를 통해 여러 개의 컨테이너를 하나의 단일 단위로 관리하고, 각 컨테이너 간의 의존성과 설정을 쉽게 관리할 수 있습니다.

일반적으로 Docker 컨테이너는 단일 서비스 또는 애플리케이션을 실행하는 데 사용되지만, 많은 애플리케이션은 여러 개의 서비스 또는 컴포넌트로 구성될 수 있습니다. 예를 들어, 웹 애플리케이션은 웹 서버, 데이터베이스, 백엔드 서비스 등 여러 컴포넌트로 구성될 수 있습니다. Docker Compose는 이러한 컨테이너들의 설정과 구성을 하나의 파일로 관리하여 개발, 테스트, 배포 과정을 단순화하고, 환경 간의 일관성을 유지할 수 있도록 도와줍니다.

Docker Compose 파일은 각 컨테이너의 이미지, 포트 매핑, 환경 변수, 볼륨 마운트 등의 설정을 정의하며, 한 번에 여러 컨테이너를 실행하고 구성할 수 있습니다. 이를 통해 개발 환경에서 운영 환경까지 일관성 있게 애플리케이션을 관리할 수 있으며, 여러 개의 서비스를 빠르게 구성하여 애플리케이션을 실행하고 테스트하는 데 유용합니다.

간단히 말하면, Docker Compose는 Docker 컨테이너 기반의 복잡한 애플리케이션을 간단하고 효율적으로 정의하고 실행하기 위한 도구입니다.

<hr>
이런 시나리오환경을 가정했을때 

![picture/Screan Shopt](picture/../../picture/scenario.png)

```yml
**DB컨테이너
docker \
run \
    --name "db" \
    -v "$(pwd)/db_data:/var/lib/mysql" \
    -e "MYSQL_ROOT_PASSWORD=123456" \
    -e "MYSQL_DATABASE=wordpress" \
    -e "MYSQL_USER=wordpress_user" \
    -e "MYSQL_PASSWORD=123456" \
    --network wordpress_net \
mysql:5.7
```

```yml
**App컨테이너
docker \
    run \
    --name app \
    -v "$(pwd)/app_data:/var/www/html" \
    -e "WORDPRESS_DB_HOST=db" \
    -e "WORDPRESS_DB_USER=wordpress_user" \
    -e "WORDPRESS_DB_NAME=wordpress" \
    -e "WORDPRESS_DB_PASSWORD=123456" \
    -e "WORDPRESS_DEBUG=1" \
    -p 8080:80 \
    --network wordpress_net \
wordpress:latest
```
#### 위 두개의 컨테이너를 각각 따로 관리해야 하지만 docker-compose를 통해서 한번에 관리 할 수 있다 뿌슝빠슝
```yml
version: "3.7" --

services:
  db:
    image: mysql:5.7
    volumes:
      - ./db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress_user
      MYSQL_PASSWORD: 123456
  
  app:
    depends_on: 
      - db
    image: wordpress:latest
    volumes:
      - ./app_data:/var/www/html
    ports:
      - "8080:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wordpress_user
      WORDPRESS_DB_PASSWORD: 123456 
```
![picture/Screan Shopt](picture/../../picture/%08docker-compose.png)
docker에선 네트워크 설정을 해서 app과 db를 연결해야 했지만 docker-compose에선 자동으로 설정이 된다.