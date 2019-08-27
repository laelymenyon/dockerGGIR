# dockerGGIR
In this repository I keep the code for building docker containers related to GGIR

To use the docker image ggir-default do:
- update the command below to specify data folder, config.csv, and output folder
- add -d if you want to make it less verbose

```
docker run -it --rm --name ggir-defaut \
--mount type=bind,source="$(pwd)"/data,target=/data \
--mount type=bind,source="$(pwd)"/config.csv,target=/config.csv \
--mount type=bind,source="$(pwd)"/output,target=/output,bind-propagation=rslave \
  vvanhees/ggir-default
```

Code inspired by [blog post](https://www.r-bloggers.com/running-your-r-script-in-docker/) by Oliver Guggenbühl. I replaced the -v command with the --mount for mounting files and folders.


Images were built and push with following commands:

```
docker build -t vvanhees/ggir-default .
docker push vvanhees/ggir-default
```
