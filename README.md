Bosh worcspace to deploy MicroBOSH to GCE
===

Description
---
This project contains folder structure and config templates to deploy MicroBOSH to Google Cloud Engine. 

Usage
---
Clone this project to `~/bosh-workspace` folder (this path is just recomentation to follow instructions in this [tutorial](http://docs.cloudfoundry.org/deploying/openstack/deploying_microbosh.html)). You can use following command `git clone https://github.com/allomov/microbosh-workspace-for-gce.git bosh-workspace`. 

After it you'll need to clone Altoros [fork](https://github.com/Altoros/bosh) of `bosh` and checkout `google-cpi-microbosh` branch. Following commands:
```
git clone https://github.com/Altoros/bosh.git -b google-cpi-microbosh ~/workspace/bosh
```

Change path to bosh folder inside [Gemfile](https://github.com/allomov/microbosh-workspace-for-gce/blob/master/Gemfile#L3). And run `bundle install` from this folder.

After that you'll need to fill in confedecial information inside [microbosh config](https://github.com/allomov/microbosh-workspace-for-gce/blob/master/deployments/microbosh-google/micro_bosh.yml). This information is required by [fog](https://github.com/fog/fog) in order to connect to GCE. All necessary information you can get from [Google Cloud Console](https://console.developers.google.com/project).

Get GCE microbosh stemcell. [Here is going to be a link to it in S3] and put it inside `stemcells` folder.

Change directory to folder with this repository and run `bosh micro deployments/microbosh-google`. This will set `deployments/microbosh-google/micro_bosh.yml` as config for MicroBOSH deployment.

After that deploy stemcell to Google Storage with following command `bosh micro deploy stemcells/<stemcell-name>.tar.gz`.

Now you are able to run `bosh deploy` to deploy Microbosh instance to Google Cloud Engine.
