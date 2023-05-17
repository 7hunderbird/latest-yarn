- Got the idea of the node image from [here](https://github.com/nodejs/docker-node/blob/main/README.md#how-to-use-this-image)

Steps to reproduce, using the `Dockerfile` in this directory:

```bash
docker build -t my-nodejs-app .
docker run -d -it --rm --name my-running-app my-nodejs-app
docker exec -it my-running-app /bin/bash
```

I tried `yarn set version latest` which only installed 1.22.19

I tried `yarn set version berry` and that installed 3.5.1

```bash
04:59:13 tylerbird@PRVLOTBIRD latest-yarn → docker run -d -it --rm --name my-running-app my-nodejs-app
a86f1c17a3a68cc78bc06f03c98a8d32546ee6ba122693acc29d0c1512437b12
05:00:04 tylerbird@PRVLOTBIRD latest-yarn → docker exec -it my-running-app /bin/bash
root@a86f1c17a3a6:/# yarn set version latest
Warning: Your current Yarn binary is currently Yarn 1.22.19; to avoid potential breaking changes, 'set version latest' won't receive upgrades past the 1.22.x branch.
         To upgrade to the latest versions, run yarn set version stable instead. Sorry for the inconvenience.

Resolving latest to a url...
Downloading https://github.com/yarnpkg/yarn/releases/download/v1.22.19/yarn-1.22.19.js...
Saving it into /.yarn/releases/yarn-1.22.19.cjs...
Updating //.yarnrc...
Done!
root@a86f1c17a3a6:/# yarn --version
1.22.19
root@a86f1c17a3a6:/# yarn set version berry 
➤ YN0000: Retrieving https://repo.yarnpkg.com/3.5.1/packages/yarnpkg-cli/bin/yarn.js
➤ YN0000: Saving the new release in .yarn/releases/yarn-3.5.1.cjs
➤ YN0000: Done in 0s 423ms
root@a86f1c17a3a6:/# yarn --version
3.5.1
root@a86f1c17a3a6:/# 
```