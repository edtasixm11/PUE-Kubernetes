# PUE Kubernetes Juliol 2020
## Curs 2020 - 2021

## Descripció de materials

 * Despliegue de Aplicaciones Kubernetes.zip
 * kubernetes-Helm3-API-Metrics-Server.zip

 * Laboratorio namespaces kubernetes.txt
 * Manual genérico guacamole (remote.pue.es) - labs.pdf
 * Seminario Docker practico para entornos DevOps.pdf
 * servicios-comunidad-educativa.pdf
 * Vagrantfile


Hi ha dos .zip que en expandir-se generen tot el material del curs. Es llista el 
contingut dels dos zips (un nivell) i també els directoris amb documentació i 
labs del seu interior que s'han usat durent el curs.

**Despliegue de Aplicaciones Kubernetes.zip**
```
Despliegue de Aplicaciones Kubernetes
├── 1-Laboratorios  Kubernetes 2020.pdf
├── 2-Laboratorios basicos kubernetes .pdf
├── cheatsheet-kubernetes-A4.pdf
├── Entorno laboratorio mv-kubernetes.txt
├── k8-for-devs-master
├── kubernetes-curso
├── Kubernetes Ingress Controllers.xlsx
├── kubernetes-labs2
├── Laboratorio-deployment-strategies
├── Laboratorio Instalar Cluster Kubernetes Alumnos
├── Laboratorios-Ejemplos-TXT
├── mv-kubernetes-Vagrant-2020
├── Seminario kubernetes estrategia de despliegue de aplicaciones.pdf
├── Seminario kubernetes.pdf
└── Seminario kubernetes Troubleshooting  Deployments Applications.pdf
```

**kubernetes-Helm3-API-Metrics-Server.zip**
```
kubernetes-Helm3-API-Metrics-Server
├── ClusterRoleBinding.yml
├── helm3  add repo stable .txt
├── helm-v3.3.1-linux-amd64.tar.gz.tar
├── metrics-server.yaml
└── service-account.yml
```

**Despliegue de Aplicaciones Kubernetes/kubernetes-curso/**
```
Despliegue de Aplicaciones Kubernetes/kubernetes-curso/
├── affinity
├── apps
├── autoscaling
├── a.yml
├── berto.yml
├── configmap
├── dashboard
├── deployment
├── elb-tls
├── external-dns
├── first-app
├── helm
├── hpa-php-apache.yml
├── ingress
├── ingress-wp.yml
├── init-containers.yaml
├── intro-to-k8s
├── istio
├── k8s-demo
├── kubeless
├── mariadb-deployment-configmap.yaml
├── mariadb-deployment-secret.yaml
├── metrics-server
├── mysql-affinity.yml
├── mysql-storage-nfs.yml
├── nfs-pv-pvc.yaml
├── pod-helloworld.yml
├── pod-lifecycle
├── pod-presets
├── postgres-operator
├── README.md
├── replication-controller
├── resourcequotas
├── service-discovery
├── service-wp-lab-yml
├── statefulset
├── tolerations
├── users
├── volumes
├── webtest-volum-emptydir.yml
├── wordpress
├── WordPress-kubernetes
└── wordpress-volumes
```

**Despliegue de Aplicaciones Kubernetes/kubernetes-labs2/**
```
Despliegue de Aplicaciones Kubernetes/kubernetes-labs2/
├── deployments
├── envs
├── healthz
├── ic
├── jobs
├── labels
├── logging
├── nodes
├── ns
├── pf
├── pods
├── pv
├── rcs
├── sd
├── secrets
├── services
└── volumes
```

**Despliegue de Aplicaciones Kubernetes/k8-for-devs-master/**
```
Despliegue de Aplicaciones Kubernetes/k8-for-devs-master/
├── deployments
├── dev
├── healthchecks
├── images
├── ingress
├── labels
├── namespaces
├── pods
├── replica-sets
├── secrets
├── services
└── voting-app
```

**Despliegue de Aplicaciones Kubernetes/Laboratorios-Ejemplos-TXT/**
```
Despliegue de Aplicaciones Kubernetes/Laboratorios-Ejemplos-TXT/
├── Añadir carga el contenedor web1.txt
├── Cambiar  contexto default en kubernetes.txt
├── Comandos kubernetes.txt
├── Dns Kubernetes.txt
├── healthcheck WildFly Kubernetes exec probes.txt
├── Install NFS Kernel Server Ubuntu.txt
├── lab deployment.txt
├── Laboratorio deployement kubernetes-martes27.txt
├── Laboratorio deployement kubernetes.txt
├── Laboratorio Deployment kubernetes comandos.txt
├── Laboratorio Deployment kubernetes.txt
├── Laboratorio Deployments por comandos.txt
├── Laboratorio-deployment-strategies.txt
├── Laboratorio ingress kubernetes con Traefick.txt
├── Laboratorio NFS wp-mysql.txt
├── Laboratorio quotas namespaces.txt
├── Lab pods.txt
├── mv-kubernetes.txt
├── mv-kubernetes-virtualbox.txt
├── Reinstalar traefik en las mv de laboratorios.txt
├── relacionar un pv con un pvc.txt
└── Trabajando con contextos.TXT
```


## Instal·lació / Desplegament

Per treballar ab un Kubernetes real el curs utilitza un desplegament en Vagrant 
preparat pel professor, hi ha dos mecanismes per fer el desplegament:
 * Descarregar el GIT del professor i desplegar Vagrant. 
 * Usar la propia estructura descarregada i usar el Vagrant que hi ha en un dels zips.


**Descarrega via GIT del professor**

Aquest procediment consisteix en:
 * [ Prèvia ] Per poder fer el desplegament cal tenir instal·lat VirtualBox i Vagrant.
 * Descarregar el GIT del professor localment generant un directori anomenat *kubernetes*. 
 * Dins d'aquest directori descomprimir tres dels fitxers zip de documentació i labs.
 * També hi ha el fitxer de desplegament *Vagrant* que generarà de manera automàtica tot el 
laboratori (els tres nodes ja configurats). Cal realitzar l'ordre *vagrant up* Aquest procés
pot fallar (per timeout), simplement tornar a insistir.
 * Un cop desplegades les tres màquines amb Vagrant connectar-se al node *Master* amb l'ordre
*vagrant ssh master* que automàticament inicia una sessió per ssh dins d'aquest node.
 * Verificar que un cop dins el Lab desplegat per Vagrant els tres nodes estan en funcionament
 i actius amb l'ordre *kubectl get nodes*. S'han de mostrar els tres nodes: master, worker1 i 
worker2.

```
git clone https://github.com/agarciafer/kubernetes.git
cd kubernetes
sudo unzip kubernetes-curso.zip
sudo unzip k8-for-devs-master.zip
sudo unzip kubernetes-labs2.zip

vagrant up
vagrant ssh master
#ssh vagrant@10.0.0.10

cd /vagrant
kubectl get nodes
```

**Desplegament usant el contingut del zip**

Per fer el desplegament amb *Vagrant* simplement cal tenir instal·lat *Virtualbox* i *Vagrant* i 
fer el desplegament usant el fitxer *Vagrantfile* ja preparat. Els passos són:
 * [ Prèvia ] Per poder fer el desplegament cal tenir instal·lat VirtualBox i Vagrant.
 * Accedir al directori *mv-kubernetes-Vagrant-2020* (dins de *Despliegue de Aplicaciones Kubernetes*) que conté el *Vagrantfile*. 
 * Fer el desplegament (des de dins del directori) amb l'ordre *vagrant up*.
 * Un cop desplegades les tres màquines amb Vagrant connectar-se al node *Master* amb l'ordre
*vagrant ssh master* que automàticament inicia una sessió per ssh dins d'aquest node.
 * Verificar que un cop dins el Lab desplegat per Vagrant els tres nodes estan en funcionament
 i actius amb l'ordre *kubectl get nodes*. S'han de mostrar els tres nodes: master, worker1 i
worker2.


```
Despliegue de Aplicaciones Kubernetes/mv-kubernetes-Vagrant-2020/
└── Vagrantfile
``` 

```
cd Despliegue de Aplicaciones Kubernetes/mv-kubernetes-Vagrant-2020/
vagrant up
vagrant ssh master
#ssh vagrant@10.0.0.10

cd /vagrant
kubectl get nodes
``` 


## Laboratori 

Aquest curs del PUE de Kubernetes utilitza un laboratori amb tres màquines Virtuals Centos
lleugeres però amb 2GB de RAM cada una. Les anomena:
  * master (10.0.0.10)
  * worker1 (10.0.0.11)
  * worker2 (10.0.0.12)

Com el seu nom indica es tracta d'un node master de kubernetes i dos nodes worker (o minions).
Aquests laboratori utilitza una xarxa software virtual amb adreça **IP 10.0.0.0/24**. El host
amfitrió té la interfície *10.0.0.1*, i els nodes la que s'indica al llistat.

Es pot accedir a cada un dels nodes de manera utomàtica usant la utilitzat de vagrant *vagrant ssh nomNode*.
Per poder treballar amb vagrant cal estar sempre dins del directori del desplegament, és a dir, el directori 
*kubernetes* que ha fet el GIT o el directori des d'on s'ha fet el *vagrant up*.

Així per exemple podem conncetar al node master i als nodes worker amb:
```
vagrant ssh master
```

```
vagrant ssh worker1
```

Per treballar amb Kerberos es fa des del node **Master** i amb l'ordre **kubectl** es governen
les accions que es volen realitzar:
```
kubectl get nodes
kubectl get all

kubectl get pods
kubectl get services
kubectl get pods, services, deploys
```


## Documentació

A part de la documentació d'aquest curs es recomana consultar:

 * GIT edtasim11 https://github.com/edtasixm11/PUE-Kubernetes
 * Kubernetes Documentation https://kubernetes.io/docs/home/
 * k8s
 * Projecte ASIX 2021-Kubernetes (Roberto / Alejandro) https://gitlab.com/edtasixm14/2021-kubernetes
 * Projecte ASIX 2020-Kubernetes-Roberto https://gitlab.com/edtasixm14/2020-kubernetes-roberto
 * Projecte ASIX 2020-Kubernetes-Marc https://gitlab.com/edtasixm14/2020-kubernetes-marc
 * Projecte ASIX 2020-Kubernetes (Jorge) https://gitlab.com/edtasixm14/2020-kubernetes
 * Getting Started with Kubernetes. Third Edition. Packt Publishing. Jonathan Baier & Jesse White.










