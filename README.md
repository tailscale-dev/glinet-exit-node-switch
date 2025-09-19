# glinet-exit-node-switch
A script from Mike O'Driscoll ([@mikeodr](https://github.com/mikeodr)) to toggle Tailscale exit nodes from a GL.iNet physical switch. This is known to work on the GL.iNet Beryl AX (MT-3000); it likely works with most other GL.iNet routers, but cannot be guaranteed. Back up your settings, use caution, and all that good stuff.

## Use:
1. Ensure you have an [exit node](https://tailscale.com/kb/1103/exit-nodes) set up in your tailnet
2. Ensure the exit node is accessible in your router's Tailscale settings (Settings > Applications > Tailscale > Custom Exit Node, enable, refresh, and note and copy IP address you've chosen)
3. [SSH into your router](https://docs.gl-inet.com/router/en/3/tutorials/ssh/) (user is `root`, password is the admin password you set)
4. Navigate to `/etc/rc.button` (`cd /etc/rc.button`)
5. Edit the `switch` script with Vim (`vim /etc/rc.button/switch`) to match the modified script switch here, or replace the script entirely, depending on your vim/ssh comfort.
6. Be sure to add your exit node IPv4 address near line 46 (`/usr/sbin/tailscale set --exit-node=100.XXX.YYY.ZZZ`)
7. You may need to reboot your router for the switch to start working; alternately, try enabling and disabling the exit node in router settings.

A good way to test your exit node switch is to point a browser on a device connected to your GL.iNet router to a site like [icanhazip](https://icanhazip.com), and see whether the IP reported changes when the switch toggles. This will not work if your GL.iNet router is receiving its connection through the same network as your exit node; try tethering your GL.iNet router to your phone's cellular connection for a quick test.
