# Most used Kubernetes & Container commands
(Docker for containers, kubectl for Kubernetes — the ones you'll actually reach for day to day)

**Container basics (Docker)**
```
1. Check docker version -> docker version
2. List running containers -> docker ps
3. List all containers (incl. stopped) -> docker ps -a
4. List images -> docker images
5. Pull an image -> docker pull image:tag
6. Run a container -> docker run image
7. Run interactively with shell -> docker run -it image /bin/bash
8. Run in background (detached) -> docker run -d image
9. Run with port mapping -> docker run -p 8080:80 image
10. Run with volume mount -> docker run -v /host/path:/container/path image
```

**Container lifecycle**
```
1. Stop a container -> docker stop <container>
2. Start a stopped container -> docker start <container>
3. Restart a container -> docker restart <container>
4. Remove a container -> docker rm <container>
5. Force remove a running container -> docker rm -f <container>
6. Remove all stopped containers -> docker container prune
7. Kill a container immediately -> docker kill <container>
```

**Inspecting containers**
```
1. View container logs -> docker logs <container>
2. Follow logs live -> docker logs -f <container>
3. Exec into a running container -> docker exec -it <container> /bin/bash
4. Inspect container details (JSON) -> docker inspect <container>
5. Show resource usage -> docker stats
6. Show container's running processes -> docker top <container>
7. Copy file from container to host -> docker cp <container>:/path /host/path
```

**Building images**
```
1. Build image from Dockerfile -> docker build -t name:tag .
2. Build without cache -> docker build --no-cache -t name:tag .
3. Tag an image -> docker tag source_image target_image
4. Remove an image -> docker rmi image
5. Remove unused images -> docker image prune
6. Remove everything unused (images/containers/networks) -> docker system prune -a
7. View image layer history -> docker history image
```

**Docker registry**
```
1. Login to a registry -> docker login
2. Push an image -> docker push image:tag
3. Pull an image (again, for reference) -> docker pull image:tag
4. Logout -> docker logout
```

**Docker Compose**
```
1. Start all services -> docker compose up
2. Start in background -> docker compose up -d
3. Stop all services -> docker compose down
4. View running services -> docker compose ps
5. View logs -> docker compose logs -f
6. Rebuild and start -> docker compose up --build
7. Run a one-off command in a service -> docker compose exec service_name command
```

**Networks & Volumes**
```
1. List networks -> docker network ls
2. Create a network -> docker network create name
3. Inspect a network -> docker network inspect name
4. List volumes -> docker volume ls
5. Create a volume -> docker volume create name
6. Remove a volume -> docker volume rm name
7. Remove unused volumes -> docker volume prune
```

---

**Kubernetes cluster basics**
```
1. Check kubectl version -> kubectl version
2. Show cluster info -> kubectl cluster-info
3. View current context -> kubectl config current-context
4. List all contexts -> kubectl config get-contexts
5. Switch context -> kubectl config use-context <name>
6. List nodes -> kubectl get nodes
7. Describe a node -> kubectl describe node <name>
```

**Pods**
```
1. List pods -> kubectl get pods
2. List pods across all namespaces -> kubectl get pods -A
3. Describe a pod -> kubectl describe pod <name>
4. View pod logs -> kubectl logs <pod>
5. Follow pod logs live -> kubectl logs -f <pod>
6. Logs of a specific container in a pod -> kubectl logs <pod> -c <container>
7. Exec into a pod -> kubectl exec -it <pod> -- /bin/bash
8. Delete a pod -> kubectl delete pod <name>
9. Get pod YAML/manifest -> kubectl get pod <name> -o yaml
```

**Deployments**
```
1. List deployments -> kubectl get deployments
2. Describe a deployment -> kubectl describe deployment <name>
3. Create/apply from a file -> kubectl apply -f deployment.yaml
4. Scale a deployment -> kubectl scale deployment <name> --replicas=3
5. Update image on a deployment -> kubectl set image deployment/<name> container=image:tag
6. Rollout status -> kubectl rollout status deployment/<name>
7. Rollout history -> kubectl rollout history deployment/<name>
8. Rollback a deployment -> kubectl rollout undo deployment/<name>
9. Delete a deployment -> kubectl delete deployment <name>
```

**Services & Networking**
```
1. List services -> kubectl get svc
2. Describe a service -> kubectl describe svc <name>
3. Expose a deployment as a service -> kubectl expose deployment <name> --port=80 --target-port=8080
4. Port-forward to local machine -> kubectl port-forward pod/<name> 8080:80
5. List ingress resources -> kubectl get ingress
6. Describe an ingress -> kubectl describe ingress <name>
```

**Namespaces & Config**
```
1. List namespaces -> kubectl get namespaces
2. Create a namespace -> kubectl create namespace <name>
3. Set default namespace for context -> kubectl config set-context --current --namespace=<name>
4. List configmaps -> kubectl get configmaps
5. List secrets -> kubectl get secrets
6. View a secret's data (base64) -> kubectl get secret <name> -o yaml
7. Create a secret from literal -> kubectl create secret generic <name> --from-literal=key=value
```

**Applying, editing & deleting resources**
```
1. Apply a manifest -> kubectl apply -f file.yaml
2. Apply an entire folder -> kubectl apply -f dir/
3. Delete resources from a manifest -> kubectl delete -f file.yaml
4. Edit a resource live -> kubectl edit deployment <name>
5. Diff before applying -> kubectl diff -f file.yaml
6. Get any resource type generically -> kubectl get <resource_type>
7. Describe any resource generically -> kubectl describe <resource_type> <name>
```

**Debugging & Troubleshooting**
```
1. Get events (cluster-wide) -> kubectl get events --sort-by=.metadata.creationTimestamp
2. Get events for a namespace -> kubectl get events -n <namespace>
3. Check resource usage (needs metrics-server) -> kubectl top pods
4. Check node resource usage -> kubectl top nodes
5. Get pod's YAML with status -> kubectl get pod <name> -o yaml
6. Run a temporary debug pod -> kubectl run debug --rm -it --image=busybox -- sh
7. Explain a resource field -> kubectl explain pod.spec.containers
```

**Contexts, RBAC & Access**
```
1. Check what you can do -> kubectl auth can-i <verb> <resource>
2. List roles -> kubectl get roles
3. List role bindings -> kubectl get rolebindings
4. List cluster roles -> kubectl get clusterroles
5. Describe a role -> kubectl describe role <name>
6. Get current user info -> kubectl config view --minify
```

**Helm (package manager for Kubernetes)**
```
1. Add a repo -> helm repo add name url
2. Update repos -> helm repo update
3. Search a repo -> helm search repo keyword
4. Install a chart -> helm install release-name chart-name
5. List installed releases -> helm list
6. Upgrade a release -> helm upgrade release-name chart-name
7. Rollback a release -> helm rollback release-name revision
8. Uninstall a release -> helm uninstall release-name
```

---

### The 80/20 shortlist
If you only remember a handful, make it these:

**Docker:** `docker ps`, `docker run -it`, `docker exec -it`, `docker logs -f`, `docker build -t`, `docker compose up -d`

**Kubernetes:** `kubectl get pods`, `kubectl describe pod`, `kubectl logs -f`, `kubectl exec -it`, `kubectl apply -f`, `kubectl get events`, `kubectl rollout status`
