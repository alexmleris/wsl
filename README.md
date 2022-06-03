<h1>Failed to connect to bus</h1>
<pre>systemctl status</pre>
> System has not been booted with systemd as init system (PID 1). Can't operate. Failed to connect to bus: Host is down 

<h2>Fix:</h2>

<pre>apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig</pre>
<pre>daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target</pre>
<pre>exec nsenter -t $(pidof systemd) -a su - $LOGNAME</pre>

<h2>Test</h2>
<pre>systemctl status</pre>
