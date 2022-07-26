Linux
========

关于Linux的各类发布版本
-----------------------------

内网文件夹的挂载
------------------------

前提条件：具有将要挂载的服务器的权限。
通过/etc/fstab配置文件添加相应的参数然后mount实现功能

.. code-block::

   sudo mkdir /the_target_mount_dir_at_local_network
   sudo chown shengbin:shengbin /the_target_mount_dir_at_local_network
   sudo echo ""192.168.185.40:/data_NAS /data_NAS nfs defaults 0 0" >> /etc/fstab
   sudo mount --all
