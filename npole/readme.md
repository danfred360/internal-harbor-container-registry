https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-top-of-digitalocean-spaces-and-use-it-with-digitalocean-kubernetes

https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nginx-ingress-on-digitalocean-kubernetes-using-helm
**Note: This tutorial has a bug**

hello-kubernetes-ingress.yaml - *tutorial version*
`
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
name: hello-kubernetes-ingress
annotations:
  kubernetes.io/ingress.class: nginx
  cert-manager.io/cluster-issuer: letsencrypt-prod
spec:
  tls:
  - hosts:
    - hw1.your_domain
    - hw2.your_domain
    secretName: hello-kubernetes-tls
  rules:
  - host: "hw1.your_domain_name"
    http:
      paths:
      - pathType: Prefix
        path: "/"
        backend:
          service:
            name: hello-kubernetes-first
            port:
              number: 80
  - host: "hw2.your_domain_name"
    http:
      paths:
      - pathType: Prefix
        path: "/"
        backend:
          service:
            name: hello-kubernetes-second
            port:
              number: 80
`

should be

hello-kubernetes-ingress.yaml - *correct version*
`
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
    name: hello-kubernetes-ingress
    annotations:
    kubernetes.io/ingress.class: nginx
    cert-manager.io/cluster-issuer: letsencrypt-prod
spec:
  tls:
  - hosts:
    - hw1.your_domain
    - hw2.your_domain
    secretName: hello-kubernetes-tls
  rules:
  - host: "hw1.your_domain_name"
    http:
      paths:
      - pathType: Prefix
        path: "/"
        backend:
          service:
            name: hello-kubernetes-first
            port:
              number: 80
  - host: "hw2.your_domain_name"
    http:
      paths:
      - pathType: Prefix
        path: "/"
        backend:
          service:
            name: hello-kubernetes-second
            port:
              number: 80
`
per kubernetes docs - [Object Names and IDs](https://kubernetes.io/docs/concepts/overview/working-with-objects/names/)

https://docs.digitalocean.com/products/kubernetes/how-to/connect-to-cluster/

https://www.digitalocean.com/community/tutorials/how-to-create-a-digitalocean-space-and-api-key

https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars
