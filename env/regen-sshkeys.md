# Regenerate SSH host keys
```bash
rm -v /etc/ssh/ssh_host_*
dpkg-reconfigure openssh-server
systemctl restart sshd
```


### Reference
* https://www.cyberciti.biz/faq/howto-regenerate-openssh-host-keys/
