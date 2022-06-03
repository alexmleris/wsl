systemctl status
>> System has not been booted with systemd as init system (PID 1). Can't operate. Failed to connect to bus: Host is down 

Solved:
apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig
daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target
exec sudo nsenter -t $(pidof systemd) -a su - $LOGNAME
systemctl status
