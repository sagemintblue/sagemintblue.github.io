---
layout: post
title: "Sorting out apt-get dist-upgrade and nvidia kernel modules on Ubuntu"
date: 2013-01-20 16:02
comments: true
categories: ubuntu
---

I ran into some trouble with my Ubuntu 12.10 machine yesterday when running a few updates; I noticed
that after a normal apt-get update/upgrade a few packages had been "kept back." Turns out `apt-get
upgrade` will refuse to remove or install new packages by default. If you want everything fully
updated, along with new transitive dependencies of existing packages, you need `apt-get
dist-upgrade` instead ([1], [2], [3], [4], [5]).

[1]: http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade
[2]: http://askubuntu.com/questions/215267/apt-get-dist-upgrade
[3]: http://askubuntu.com/questions/216371/apt-get-dist-upgrade-doesnt-fix-the-following-packages-have-been-kept-back
[4]: http://superuser.com/questions/386583/will-apt-get-dist-upgrade-update-my-ubuntu-to-the-next-major-release
[5]: http://ubuntulinuxtipstricks.blogspot.com/2010/02/dist-upgrade-misnomer-confusion.html

Unfortunately, when I ran `apt-get dist-upgrade` it upgraded my system's kernel but didn't recompile
existing kernel modules to work with it. The nvidia driver / kernel module failed to load on reboot,
causing the display manager and X to enter some awful video mode. Looks like others have run into
this issue before ([6], [7]). To get things back in order, I followed roughly these steps:

[6]: http://askubuntu.com/questions/173721/how-do-i-update-my-nvidia-modules-after-updating-my-kernel
[7]: http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal

{% highlight sh %}
# Get to a shell on the machine
ssh yourbrokenbox

# Ensure `jockey-text` is available so you can control proprietary drivers (e.g. `nvidia-current`)
# from the command line. If you don't have it, try installing one of jockey's graphical front end
# packages, for example:
sudo apt-get install jockey-gtk

# Turn off the display manager (and X)
sudo stop lightdm

# Turn off the nvidia module
sudo dkms remove nvidia

# Completely remove the nvidia driver package (in my case `nvidia-current`)
sudo apt-get remove --purge nvidia-current

# Make sure you have the latest headers with which to rebuild the driver
sudo apt-get install linux-headers-generic

# Reinstall and rebuild the driver with current kernel
sudo apt-get install nvidia-current

# Check to see if the driver was enabled during install
sudo jockey-text -l

# If necessary, enable the driver
sudo jockey-text -e kmod:nvidia-current

# Reboot and check `/var/logs/Xorg.0.log` and friends for errors
sudo shutdown -r now
{% endhighlight %}
