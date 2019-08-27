# dockerGGIR
In this repository I keep the code for building docker containers related to GGIR

### There are two docker images on Dockerhub:
- vvanhees/base-r-ggir:GGIR1.10-1, which has R base and GGIR
- vvanhees/ggir-default, which uses the beforementioned image to facilitate application of GGIR to data

Images were built and pushed to Dockerhub with following commands:

```
docker build -t vvanhees/ggir-default .
docker build -t vvanhees/base-r-ggir .
docker push vvanhees/ggir-default
docker push vvanhees/base-r-ggir:GGIR1.10.1
```


### To use the docker image ggir-default do:
- Update the command below to specify data folder, this folder needs to contain accelerometer data files
- The config.csv file can be produced with GGIR, an [example file
(config.csv) is include in this repo.
- The output folder needs to exist, and should not be equal to or a sub-directory of the data folder.
- Add -d if you want to make it less verbose

```
docker run -it --rm --name ggir-defaut \
--mount type=bind,source="$(pwd)"/data,target=/data \
--mount type=bind,source="$(pwd)"/config.csv,target=/config.csv \
--mount type=bind,source="$(pwd)"/output,target=/output,bind-propagation=rslave \
  vvanhees/ggir-default
```

Acknowledgment: Code inspired by [blog post](https://www.r-bloggers.com/running-your-r-script-in-docker/) by Oliver Guggenbühl. I replaced the -v command with the --mount for mounting files and folders.
