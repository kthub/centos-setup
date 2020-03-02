### Install ansible
```
# yum -y install ansible
```
### Run a playbook
CentOS環境を払い出す際のIPアドレスは`-e`オプションで指定する。
```
# ansible-playbook -i inventory -e '{"ip_addr":"192.168.1.205"}' cicd-playbook.yml
```
