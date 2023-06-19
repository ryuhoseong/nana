### debug mode
    /usr/sbin/sshd -d -p 22

### sftp 접속 이슈
```
    subsystem: cannot stat /usr/libexec/openssh/sftp-server: No such file or directory
    subsystem request for sftp failed, subsystem not found
```
```
    vi /etc/ssh/sshd_config
    
    아래의 구문으로 변경
    # Subsystem sftp /usr/lib/openssh/sftp-server    
    Subsystem sftp internal-sftp
```