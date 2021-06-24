# Create All Images
```bash
kp image create asp-dotnet-demo --tag harbor.terasky.demo/tbs-demo-images/asp-dotnet-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/asp-dotnet/
kp image create dotnet-core-demo --tag harbor.terasky.demo/tbs-demo-images/dotnet-core-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/dotnet-core
kp image create go-demo --tag harbor.terasky.demo/tbs-demo-images/go-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/go
kp image create java-springboot-gradle-demo --tag harbor.terasky.demo/tbs-demo-images/java-springboot-gradle-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/java-springboot-gradle
kp image create node-demo --tag harbor.terasky.demo/tbs-demo-images/node-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/node
kp image create node-tsc-demo --tag harbor.terasky.demo/tbs-demo-images/node-tsc-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/node-tsc
kp image create node-yarn-demo --tag harbor.terasky.demo/tbs-demo-images/node-yarn-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/node-yarn
kp image create procfile-demo --tag harbor.terasky.demo/tbs-demo-images/procfile-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/procfile
kp image create python-demo --tag harbor.terasky.demo/tbs-demo-images/python-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/python
```

# Deploy all images

1. Create a bash file with the following contents and run it
``` bash
kubectl get image --no-headers -o custom-columns=":status.latestImage" > /tmp/imageRefs.txt
mkdir -p ./k8s-manifests

while read img
do
  name=`echo $img | cut -d '/' -f 3 | cut -d '@' -f 1`
  cat << EOF > ./k8s-manifests/$name.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: $name
  name: $name
spec:
  replicas: 1
  selector:
    matchLabels:
      app: $name
  strategy: {}
  template:
    metadata:
      labels:
        app: $name
    spec:
      containers:
      - image: $img
        name: $name
        ports:
        - containerPort: 8080
---
apiVersion: v1
kind: Service
metadata:
  labels:
    app: $name
  name: $name
spec:
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: 8080
  selector:
    app: $name
  type: LoadBalancer
---
apiVersion: projectcontour.io/v1
kind: HTTPProxy
metadata:
  name: $name
spec:
  virtualhost:
    fqdn: $name.terasky.demo
  routes:
    - conditions:
      - prefix: /
      services:
        - name: $name
          port: 80
EOF
done < /tmp/imageRefs.txt
```
2. run the following command
```bash
kubectl apply -f ./k8s-manifests/
```

# Delete All Images
```bash
kp image delete asp-dotnet-demo
kp image delete dotnet-core-demo
kp image delete go-demo
kp image delete java-springboot-gradle-demo
kp image delete node-demo
kp image delete node-tsc-demo
kp image delete node-yarn-demo
kp image delete procfile-demo
kp image delete python-demo
```
