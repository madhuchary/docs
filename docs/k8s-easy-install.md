---
id: k8s-easy-install
title: Installing kubernetes from scratch 
---
## Installing kubernetes the easy way
## In our example we use Ubuntu AWS EC2 instances  
Step 1. Launch 2 instances
  * Master - t2.medium
  * worker-0 - t2.micro

Step 2. Install openssl on Master

export all the IP addresses and hostnames of master and workers

```
export INT_MASTER_IP_0=<master-private-ip>
export INT_WORKER_IP_0=<worker-private-ip>
export EXT_MASTER_IP_0=""
export EXT_WORKER_IP_0=""
export MASTER_HOSTNAME=""
export DNS_NAME=""
```

Step 3. Generate certificates for all kubernetes components

* Generate RootCA

```
openssl genrsa -out rootCA.key 4096
openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 1024 -out rootCA.crt
```

* Create script for automating cert generation 

```
cat <<EOF > csrtest.conf
[ req ]
default_bits = 2048
prompt = no
default_md = sha256
req_extensions = req_ext
distinguished_name = dn

[ dn ]
C = US
ST = California
L = Fremont
O = Gamyam Learn
OU = Learn
CN = CN_NAME

[ req_ext ]
subjectAltName = @alt_names

[ alt_names ]
DNS.1 = kubernetes
DNS.2 = kubernetes.default
DNS.3 = kubernetes.default.svc
DNS.4 = kubernetes.default.svc.cluster
DNS.5 = kubernetes.default.svc.cluster.local
IP.1 = 127.0.0.1
IP.2 = $INT_MASTER_IP_0
IP.3 = $INT_WORKER_IP_0
[ v3_ext ]
authorityKeyIdentifier=keyid,issuer:always
basicConstraints=CA:FALSE
keyUsage=keyEncipherment,dataEncipherment
extendedKeyUsage=serverAuth,clientAuth
subjectAltName=@alt_names

EOF
```
```
cat <<EOF > gen_cert.sh
#!/bin/bash
#usage: gen_cert.sh sub_name common_name
openssl genrsa -out \${1}.key 2048
sed  "s/CN_NAME/\$2/" csrtest.conf > csr.conf
openssl req -new -key \${1}.key -out \${1}.csr -config csr.conf
openssl x509 -req -in \${1}.csr -CA rootCA.crt -CAkey rootCA.key \
-CAcreateserial -out \${1}.crt -days 700 \
-extensions v3_ext -extfile csr.conf
EOF

```
* Generate admin user certificates

```
bash gen_certs.sh admin admin
```

* Generate kubelet certs for all workernodes

```
bash gen_certs.sh worker-0 system:node:172.31.89.32
```

* Generate kube-controller-manager certificates
```
bash gen_certs.sh kube-controller-manager system:kube-controller-manager
```

* Generate kube-proxy certificates
```
bash gen_certs.sh kube-proxy system:kube-proxy
```
* Generate kube-scheduler certificates
```
bash gen_certs.sh kube-scheduler system:kube-scheduler
```
* Generate API certificates
```
bash gen_certs.sh kube-api kubernetes
```
* Generate service-accounts certificates
```
bash gen_certs.sh service-accounts service-accounts
```

