# NOTA esta configuración es de prueba y no podrá utilizarse en producción.
# Esta configuración no es una recomendación de ansible
ansible-playbook sudoers.yaml -i inventory.yaml

ansible -m shell -a "rm /etc/sudoers.d/90-sudoers-app-config" -i inventory.yaml all --become 

ansible -m shell -a "userdel -r -f xpkuser" -i inventory.yaml all --become 
