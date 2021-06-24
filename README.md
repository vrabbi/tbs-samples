## Tanzu Build Service Samples Repo
This repository contains sample implementations of the core components of the [Cloud Native Buildpacks](https://buildpacks.io/) (CNB) project for learning and testing purposes.

Includes:

- [Apps](apps/)

### Start here:
1. Go into the apps directory to view the different language examples

### Creating an Image:
1. Clone this repo:
```bash
git clone https://github.com/vrabbi/tbs-samples.git
```

2. Enter into one of the example folders under the apps directory:
```bash
cd samples/apps/<EXAMPLE_FOLDER>
```

3. Run the following command to create an image:
``` bash
# for procfile, java, node, dotnet, go nginx and python use the following command as is
# for php you must add "--cluster-builder full" as the php buildpack is not in the default cluster builder
kp image create <IMAGE_NAME> --tag <CONFIGURED_IMAGE_REPO>/<IMAGE_NAME> --git https://github.com/vrabbi/tbs-samples --git-revision master --sub-path ./apps/<EXAMPLE_FOLDER>/ --wait
```
