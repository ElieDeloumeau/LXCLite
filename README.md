LXC Lite
========

A small python library for LXC

> Tested with : LXC 0.8 and 0.9 on Ubuntu 12.04, Ubuntu 12.10 and Ubuntu 13.04

**Author: Elie Deloumeau**

**Contact: elie@deloumeau.fr**

Installation
============

    git clone https://github.com/googley/LXCLite.git

Usage
=====

**You can import lxclite as lxc (for faster usage)**

example:

    >>> import lxclite as lxc
    >>> lxc.xxxx()

**Create container:**

The simple way *(default template is Ubuntu)*:

    >>> lxc.create('container1')
    >>> 0

With all options:

    >>> lxc.create('container1', template='ubuntu', storage='--vgname foo --lvname bar', xargs='template command')
*Returns shell error code. 0 is good!*

**Clone container:**

    >>> lxc.clone(orig='container1', new='container2', snapshot=False)
    >>> 0
*Returns shell error code. 0 is good!*
    
**Check if container exist:**

    >>> lxc.exists('container1')
    >>> True
*Returns True if exists and False if not.*

**Get container infos:**

    >>> lxc.info('container1')
    >>> {'state': 'STOPPED',
        'pid': '1863'}

**List containers:**

    >>> lxc.ls()
    >>> ['container1', 'container2']

**List containers with states:**

    >>> lxc.listx()
    >>> {'RUNNING': [],
        'FROZEN': [],
        'STOPPED': ['container1', 'container2']}
        
**List running containers:**

    >>> lxc.running()
    >>> []
    
**List frozen containers:**

    >>> lxc.frozen()
    >>> []

**List stopped containers:**

    >>> lxc.stopped()
    >>> ['container1', 'container2']
    
**Start container:**

    >>> lxc.start('container1')
    >>> 0
*Returns shell error code. 0 is good!*

**Stop container:**

    >>> lxc.stop('container1')
    >>> 0
*Returns shell error code. 0 is good!*

**Restart container:**

    >>> lxc.restart('container1')
    >>> 0
*Returns shell error code. 0 is good!*

**Freeze/Unfreeze container:**

    >>> lxc.freeze('container1')
    >>> 0
    >>>
    >>> lxc.unfreeze('container1')
    >>> 0
*Returns shell error code. 0 is good!*

**Destroy container:**

    >>> lxc.destroy('container2')
    >>> 0
*Returns shell error code. 0 is good!*

**Check kernel config:**

    >>> lxc.checkconfig()
    >>> ['Kernel config /proc/config.gz not found, looking in other places...', 'Found kernel config file /boot/config-3.5.0-21-generic', '--- Namespaces ---', 'Namespaces:enabled', 'Utsname namespace:enabled', 'Ipc namespace:enabled', 'Pid namespace:enabled', 'User namespace:missing', 'Network namespace:enabled', 'Multiple /dev/pts instances:enabled', '', '--- Control groups ---', 'Cgroup:enabled', 'Cgroup clone_children flag:enabled', 'Cgroup device:enabled', 'Cgroup sched:enabled', 'Cgroup cpu account:enabled', 'Cgroup memory controller:enabled', 'Cgroup cpuset:enabled', '', '--- Misc ---', 'Veth pair device:enabled', 'Macvlan:enabled', 'Vlan:enabled', 'File capabilities:enabled', '', 'Note :Before booting a new kernel, you can check its configuration', 'usage :CONFIG=/path/to/config /usr/bin/lxc-checkconfig', '', '']

**Change cgroup values:**

    >>> lxc.cgroup('container1', 'lxc.cgroup.memory.limit_in_bytes', '256M')
    >>> 0
*Returns shell error code. 0 is good!*
