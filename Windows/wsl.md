#### 색이 없을때
    source ~/.bashrc

    echo "source ~/.bashrc" >> ~/.bash_profile

### System has not been booted with systemd as init system (PID 1). Can’t operate. Failed to connect to bus: Host is down
    sudo -b unshare --pid --fork --mount-proc /lib/systemd/systemd --system-unit=basic.target
    sudo -E nsenter --all -t $(pgrep -xo systemd) runuser -P -l $USER -c "exec $SHELL"