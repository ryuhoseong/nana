### jar 백그라운드 실행
- nohup.log 생성  
    nohup java -jar [jar 파일명] &  
- nohup.log 미생성  
    nohup java -jar [jar 파일명] </dev/null &>/dev/null &  
    nohup java -jar [jar 파일명] > /dev/null 2>&1 &

### argument 넘기기
    java -jar [jar] "[args01]" "[args02]"