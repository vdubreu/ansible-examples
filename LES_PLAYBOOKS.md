# Les Playbooks

## Mise en place des containers et du fichier inventory
Demarrer des containers pour simuler plusieurs machines   
``docker run -d --name target1 systemdevformations/ubuntu_ssh
  docker run -d --name target2 systemdevformations/centos_ssh
  docker run -d --name target3 systemdevformations/alpine_ssh``
Retrouver l'adresse ip des containers
Faire un docker ps   

```
CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS                    PORTS               NAMES
b696423c6b9b        systemdevformations/alpine_ssh   /entrypoint.sh         12 minutes ago      Up 12 minutes             22/tcp              target3  
51d42febdc76        systemdevformations/centos_ssh   /usr/bin/supervisor…   12 minutes ago      Up 12 minutes (healthy)   22/tcp              target2
4bc05c32d342        systemdevformations/ubuntu_ssh   /usr/sbin/sshd -D     13 minutes ago      Up 13 minutes             22/tcp              target1  
```  

 et par container    
 ```docker inspect target1 | grep IPA```  
 ```docker inspect target2 | grep IPA```  
 ```docker inspect target3 | grep IPA ```

Faire un git fork et clone de ce repo  
```git clone  <http votre repo forke>```

Depuis la directory /ansible-examples faire ``cp inventory ..``
et modifier le fichier inventory copie precedement
dans vi faire une substition
```:1,$s/=xxx/<le password prevu pour le cours>/```
 
en fonction de vos adresses IP fourni en cours 
modifier egalement la VM centos-remote
  
 
## Installation de VirtualEnv Python et Test Ad-Hoc commande

Dans votre home directory, faire
`` python3 -m venv venv``  
cela installe le virtualenv Python dans la directory venv  
Faire  
```source venv/bin/activate``` 
Votre prompt change 
```(venv) [centos@ansible-oxiane-controller-2 ~]$```  
Faire   
```pip3 install wheel```
qui install le package wheel qui gere les package Pypi    
et
```pip3 install ansible```
et faire la commande Ansible Ad-Hoc 
```ansible all -m ping -i inventory```

## Presentation des groupes
dans la directory ansible-examples copiez le fichier inventory children 
vers votre home directory. 
et modifier les password et adresse IP 

## Premier script YAML
dans la directory ansible-examples editez le fichier ansible_ping.yml

## Premiere commande ansible-playbook
 ```ansible-playbook  -i ../inventory ansible_ping.yml  --limit centosdocker```
 ```ansible-playbook  -i ../inventory ansible_ping.yml  --limit centos```

## Ad-Hoc commande pour afficher les facts 
```ansible target2 -i ../inventory -m setup```









