Slight modification of this article placing the service behind an ingress controller.

The deployment steps are the same, except I've created one additional manifest called frontend-ingress.yaml which should be deployed last:

https://kubernetes.io/docs/tutorials/stateless-application/guestbook/