# Rathole Operator Helm Chart

[Rathole Operator](https://github.com/crmin/rathole-operator)

## Values

```yaml
crdVersion: v1alpha1

serviceAccount:
  create: true
  name: rathole-operator

replicaCount: 1

image:
  repository: crmin/rathole-operator
  pullPolicy: IfNotPresent
  tag: "v1alpha1"

affinity: {}
nodeSelector: {}

resources:
  limits:
    cpu: 500m
    memory: 128Mi
  requests:
    cpu: 10m
    memory: 64Mi

namespace:
  create: true
  name: system

imagePullSecrets: []
livenessProbe:
  httpGet:
    path: /healthz
    port: 8081
  initialDelaySeconds: 15
  periodSeconds: 20
readinessProbe:
  httpGet:
    path: /readyz
    port: 8081
  initialDelaySeconds: 5
  periodSeconds: 10
```