## Ubuntu使用ROOT用户登录

1. 普通用户登录系统，打开终端，输入sudo passwd root

2. 设置root密码

3. 重复设置root密码

4. 修改/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf的权限为777

   ``` 
   sudo  chmod  777  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
   ```

5. 打开文件

   ```
   vi  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
   ###在文件中添加
   autologin-user=root
   greeter-session=unity-greete
   greeter-show-manual-login=true
   allow-guest=false 
   autologin-user=root #Root用户登录
   autologin-session=lightdm-autologin #设置自动登录界面
   ```

6. 打开/root/.profile ，修改```mesg n || true``` 为   ```tty  -s&mesg n```

7. 重启.profile  ,   source /root/.profile

8. 打开文件/etc/pam.d/gdm-autologin ， /etc/pam.d/gdm-autologin

   ```
   注释掉 auth required pam_succeed_if.so user != root quiet_success
   ```

9. 重启

