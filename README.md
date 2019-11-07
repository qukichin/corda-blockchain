# corda-blockchain-deploy

## Description
利用Ansible快速部署Corda区块链分布式账本

## 通过Ansible来安装Corda

Ansible流程

- 首先会安装一些依赖，如JDK 
- 为Corda创建程序用户和目录 
- 为Corda节点创建systemd管理
- 准备Corda节点的配置文件 (*node.conf*)
- 安装Corda 
- 一些可选节点是需要注册的

## Role变量

所有变量都在defaults/main.yml中更改

|  variable | default value | usage |
| --- | --- | --- |
| corda_admin_email | "qukichin@163.com" | 管理员的电子邮箱 |
| corda_devmode | "true" | 定义节点是否处于“开发模式” (see notes) |
| corda_dir_location | /opt/corda | 要安装Corda的目录 |
| corda_host_p2p | "{{ ansible_hostname }}" | 节点导出到网络映射 |
| corda_host_rpc | 0.0.0.0 | 本地rpc |
| corda_initial_registration | false | 是否向Doorman注册节点 (see notes) |
| corda_java | openjdk | 选择Java (see notes) |
| corda_java_options | -Xmx2048 | Java的额外参数 |
| corda_local_path | "" | 复制到本地文件的路径 (see notes) |
| corda_name_city | London | Legal Name in node.conf |
| corda_name_country | GB | Legal Name in node.conf |
| corda_name_org | Corda | Legal Name in node.conf |
| corda_name_org_unit | Corda | (not in use) can be part of Legal Name in node.conf |
| corda_notary_type | "non_validating" | notary (see notes) |
| corda_password_keystore |  | 节点密钥存储的值，应该用Ansible Vault加密 |
| corda_password_truststore | password | truststore shared密码 |
| corda_port_p2p | 10002 | peers端口 |
| corda_port_rpc | 10003 | rpc端口 |
| corda_port_rpc_admin | 10004 | rpc管理端口 |
| corda_port_h2 | 11000 | H2端口 |
| corda_role | node | corda.jar |
| corda_rpc | disable | 定义是否应该启用RPC (see notes)|
| corda_rpc_user | corda | RPC连接的用户 |
| corda_rpc_password | corda_is_awesome | RPC用户的密码 |
| corda_source | maven | source of corda.jar (see notes) |
| corda_url_doorman | "http://example-change.it" | URL for Zone Doorman (not for devmode) |
| corda_url_networkmap | "http://example-change.it" | URL for Zone Network Map (not for devmode ) |
| corda_user | corda | 程序用户 |
| corda_version | 3.3 | Corda版本 |

## 运行
- `$ ansible-playbook -i hosts corda.yml`

