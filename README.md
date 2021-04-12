## Background

This is an active (and not yet complete) project where I'm testing out Kubernetes deployments for Elasticsearch, and approaches for easily migrating from Rancher.

## Notes from Testing

### Initializing Rancher

To initialize Rancher on one of the nodes:
```
docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher:v2.3.2
```
Firewall ports for the Rancher server:
```
firewall-cmd --add-port 80/tcp --permanent
firewall-cmd --add-port 443/tcp --permanent
```
Firewall ports for Rancher nodes:
```
firewall-cmd --add-port 2379/tcp --permanent
firewall-cmd --add-port 2380/tcp --permanent
firewall-cmd --add-port 6443/tcp --permanent
firewall-cmd --add-port 10250/tcp --permanent
firewall-cmd --add-port 10251/tcp --permanent
firewall-cmd --add-port 10252/tcp --permanent
firewall-cmd --add-port 10257/tcp --permanent
firewall-cmd --add-port 10259/tcp --permanent
firewall-cmd --add-port 8472/udp --permanent
```
Finally:
```
firewall-cmd --reload
```
