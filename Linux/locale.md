### 일시적 변경
#### 언어
    locale

#### locale 목록 확인
    locale -a
    locale -a -v

#### locale 경로
    ls /usr/lib/locale/

#### 세션 변경
    LANG=en_US

### 영구적으로 변경
    vi /etc/locale.conf
    #LANG="ko_KR.UTF-8"
    LANG=C.utf8