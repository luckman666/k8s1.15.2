# centos7 deploy_Kubernetes-v1.15.1
k8s 1.15.1一键部署地址：https://github.com/luckman666/k8s1.15.1

k8s 1.15.0一键部署地址：https://github.com/luckman666/deploy_Kubernetes-v1.15.0

k8s 1.14.1一键部署地址：https://github.com/luckman666/deploy_Kubernetes-v1.14.1

k8s 1.13.1一键部署地址：https://github.com/luckman666/deploy_Kubernetes-v1.13.1



优化了部分代码！

觉得不错给个star哦！！
注意事项：

1、只需要在修改base.config里面的固定参数即可。

2、给.sh结尾的脚本赋权限。

3、然后只需执行./k8s1.15.1.sh就可以啦！

4、tail -f setup.log 查看日志

5、物理机不用说了，要是虚拟机cpu必须最少是2个哦！切记



# 部署k8s集群具体实现步骤：

git clone https://github.com/luckman666/k8s1.15.1.git

cd k8s1.15.1 && chmod -R 755 .

编辑base.config里面的参数

./k8s1.15.1.sh


# base.config参数介绍：

masterIP：

masterip="192.168.1.107"

K8S版本：

k8s_version="v1.15.1"

服务器root密码

root_passwd=root123

多台主机的主机名前缀，主节点就叫k8s1，node叫k8s2依次后推

hostname=k8s

集群服务器IP地址

hostip=（
192.168.1.107
192.168.1.108
192.168.1.109
）
再部署的时候严格按照我所给的示例参数写哦。换参数不要换格式，以免出错

# 部署完后进入到dashboard文件夹部署dashboard

cd dashboard

kubectl create -f .

然后查看部署情况以及登录的node节点端口

kubectl get service --all-namespaces | grep kubernetes-dashboard

例如结果：
kube-system   kubernetes-dashboard   NodePort    10.101.25.47   <none>        443:31660/TCP   22m
那么你就输入https://nodeIP:31660来登录
	
查看登录时候的token

kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

关注公众号回复：k8s   获得k8s各个版本的一键部署脚本

![index4](https://github.com/luckman666/devops_kkit/blob/master/gzh.jpg)
