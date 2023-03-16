사설 인증서
=============

### 생성
    [jdk 경로]/bin/keytool -genkey -alias [[alias 명칭]] -keyalg RSA -keystore [명칭].jks  
    [jdk 경로]/bin/keytool -export -alias [alias 명칭] -keystore [명칭].jks -rfc -file [명칭].cer  
    [jdk 경로]/bin/keytool -import -alias [alias 명칭] -file [명칭].cer -keystore [명칭].ts  

### 내용 확인
    [jdk 경로]/bin/keytool -list -v -keystore [명칭].jks -alias [alias 명칭]  
    openssl x509 -in [명칭].cer -noout -text    