### 상태
    service docker status

### 실행
    service docker start

### image 다운로드 및 실행
    docker run --name tomcat8.5 -p 8080:8080 tomcat:8.0

### Dockefile 작성
ex)
```
FROM openjdk:8-jdk-alpine
WORKDIR /home/user
ADD [압축파일.tar.gz] /home/user
CMD java -Dspring.profiles.active=[application] -jar [jar명]
```
    FROM: BASE image 지정
    WORKDIR: 컨테이너 작업 디렉토리
    ADD: COPY 기능에 압축 해체 포함
    COPY: 호스트에서 컨테이너로 파일 복사
    CMD: 컨테이너에서 실행한 명령어

### image 만들기
    docker build -t [name] [경로]    

### container 실행
    docker run -it -p [외부포트]:[내부포트] --name [container명] [image명] /bin/bash

### container 실행 - mount volumn
    docker run -v $(pwd):[container 경로] -it --name [container명] [image명] /bin/bash   

### container 실행 - host network
    docker run --network host --name [container명] [image명] /bin/bash

### container 제약조건
    docker run -it -d --cpuset-cpus=0 --memory=2g -p [외부포트]:[내부포트] --name [container명] [image명] /bin/bash
### container 정보
    https://docs.docker.com/config/containers/resource_constraints/
    docker inspect <container_name> 
    제약조건 확인 가능
### docker container 상태
    docker stats

### container 삭제
    docker rm [CONTAINER_ID]

### image 삭제
    docker rmi [IMAGE_ID]

### sudo 없이 실행
    unset DOCKER_HOST

### container 리스트
    docker ps -a

### container 실행
    docker start [CONTAINER_ID]

### container 접속
    docker exec -it [CONTAINER_ID] /bin/bash

### Image가 Alpine 일때
    docker exec -it [CONTAINER_ID] /bin/sh

### container root 접속
    docker exec -u 0 -it [CONTAINER_ID] /bin/bash    

### log 출력
    docker logs -f [CONTAINER_ID]

### docker load image by tar
    docker load -i [tar파일명]                           

### container backup
    docker commit [CONTAINER_ID] [backup명]
    docker save -o [backup명].tar [backup명]
    
