# glinet-exit-node-switch
A script from Mike O'Driscoll to toggle Tailscale exit nodes from a GL.iNet physical switch. This is known to work on the GL.iNet Beryl AX (MT-3000); it likely works with most others, but cannot be guaranteed. Back up your settings, use caution, and all that good stuff.

## Use:
1. Ensure you have an [exit node](https://tailscale.com/kb/1103/exit-nodes) set up in your tailnet
2. Ensure the exit node is accessible in your router's Tailscale settings (Settings > Applications > Tailscale > Custom Exit Node, enable, refresh, and note and copy IP address you've chosen)
3. [SSH into your router](https://docs.gl-inet.com/router/en/3/tutorials/ssh/) (user is `root`, password is the admin password you set)
4. Navigate to `/etc/rc.button/switch` (`cd /etc/rc.button/switch`)
5. Edit the `switch` script with Vim (`vim /etc/rc.button/switch`) to match the modified script switch here, or replace the script entirely, depending on your vim/ssh comfort.
6. Be sure to add your exit node IPv4 address (`100.xxx.yyy.zzz`); alternately, replace it entirely.
