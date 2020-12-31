
## Generate some traffic

Let's deploy a simple traffic generator pod

```
kubectl apply -f .\traffic-generator.yaml

# get a terminal to the traffic-generator
kubectl exec -it traffic-generator sh

# install wrk
apk add --no-cache wrk

# simulate some load
wrk -c 5 -t 5 -d 99999 -H "Connection: Close" http://application-cpu

