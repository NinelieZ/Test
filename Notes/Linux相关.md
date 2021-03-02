## ssh配置免登录
    客户机 ssh-keygen -t rsa
    服务器 touch ~/.ssh authorized_keys
          chmod 0644 ~/.ssh/authorized_keys
    把rsa.pub内容拷贝到authorized_keys中

    客户机为Linux时
    ssh-copy-id 

    或
    cat ~/.ssh/id_rsa.pub | ssh demo@address -pPort "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"

    https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2

## 配置GitHub免密登录
    将*.pub中的内容复制保存到GitHub里的ssh key
    测试连通性
        ssh -T git@github.com
    之后clone时要用git的网址而非https

## VirtualBox 共享目录设置
    1.在VBoxManager中设置共享文件夹
    2.将用户添加到vboxsf用户组
        sudo adduser username vboxsf
    3.修改fstab
        sudo nano /etc/fstab
      添加
        shared_dir local_dir vboxsf defaults 0 0
      验证 若无错误则配置正确，重启后仍然有效
        sudo mount -a


