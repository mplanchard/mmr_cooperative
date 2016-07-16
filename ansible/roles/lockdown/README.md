# Lockdown role

This role secures a server by ensuring that `ufw` and `fail2ban` are
installed (on Ubuntu), and that traffic to all ports except 22 is shut
down. It also disables password login to prevent brute force attacks and
disables root login for an additional layer of security.

Additional open ports can be configured by setting the 
`extra_open_ports` host_var or group_var.
