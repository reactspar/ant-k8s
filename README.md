- kubectl apply -f deploy.yml -f svc-local.yml
- kubectl get nodes|pods|svc|deployments
- kubectl get deployment|pod|svc some-deployment
- kubectl delete svc|pod|deployment <name>
- kubectl logs -f <POD_NAME>
- kubectl rollout status deployment qsk-deploy

- kompose --file docker-compose-all.yml convert



** CTL - Command Talking Language. Pronounced: control. So, kubectl is pronounces as coob-control.


** Kafka
- kafka-topics --bootstrap-server kafka-1:29092 --list
- kafka-console-consumer  --from-beginning  --bootstrap-server kafka-1:29092 --topic antonChat2

https://blog.datumo.io/setting-up-kafka-on-kubernetes-an-easy-way-26ae150b9ca8

https://www.confluent.io/blog/kafka-listeners-explained/

https://learnk8s.io/kafka-ha-kubernetes#kafka-partitions-and-replication-factor