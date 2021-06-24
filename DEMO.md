# Create All Images
```bash
kp image create asp-dotnet-demo --tag harbor.terasky.demo/tbs-demo-images/asp-dotnet-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/asp-dotnet/
kp image create dotnet-core-demo --tag harbor.terasky.demo/tbs-demo-images/dotnet-core-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/dotnet-core
kp image create go-demo --tag harbor.terasky.demo/tbs-demo-images/go-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/go
kp image create java-gradle-demo --tag harbor.terasky.demo/tbs-demo-images/java-gradle-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/java-gradle
kp image create java-mvn-demo --tag harbor.terasky.demo/tbs-demo-images/java-mvn-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/java-mvn
kp image create java-springboot-gradle-demo --tag harbor.terasky.demo/tbs-demo-images/java-springboot-gradle-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/java-springboot-gradle
kp image create nginx-demo --tag harbor.terasky.demo/tbs-demo-images/nginx-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/nginx
kp image create node-demo --tag harbor.terasky.demo/tbs-demo-images/node-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/node
kp image create node-tsc-demo --tag harbor.terasky.demo/tbs-demo-images/node-tsc-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/node-tsc
kp image create node-yarn-demo --tag harbor.terasky.demo/tbs-demo-images/node-yarn-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/node-yarn
kp image create procfile-demo --tag harbor.terasky.demo/tbs-demo-images/procfile-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/procfile
kp image create python-demo --tag harbor.terasky.demo/tbs-demo-images/python-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/python
kp image create php-composer-demo --cluster-builder full --tag harbor.terasky.demo/tbs-demo-images/php-composer-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/php-composer
kp image create php-webserver-demo --cluster-builder full --tag harbor.terasky.demo/tbs-demo-images/php-webserver-demo --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/php-webserver
```

# Delete All Images
```bash
kp image delete asp-dotnet-demo
kp image delete dotnet-core-demo
kp image delete go-demo
kp image delete java-gradle-demo
kp image delete java-mvn-demo
kp image delete java-springboot-gradle-demo
kp image delete nginx-demo
kp image delete node-demo
kp image delete node-tsc-demo
kp image delete node-yarn-demo
kp image delete php-composer-demo
kp image delete php-webserver-demo
kp image delete procfile-demo
kp image delete python-demo
```
