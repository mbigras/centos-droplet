# Centos Droplet

> Create a DigitalOcean Droplet running CentOS

## Usage

```
ssh-keygen -q -b 2048 -t rsa -N '' -f id_rsa
export TF_VAR_do_token="$(lpass show --notes do_token)"
terraform init
terraform plan
terraform apply -auto-approve
ansible-playbook playbook.yml
ip=$(terraform state show digitalocean_droplet.web | awk '/ipv4_address/ { print $NF }')
ssh -i id_rsa root@$ip echo hello world
terraform destroy -force
rm id_rsa*
```