# docker-GGIR
Code for building docker containers with GGIR

Most of the code in this repository was inspired by
https://www.r-bloggers.com/running-your-r-script-in-docker/
but I replaced the -v command with the --mount.


For my own reference:
docker build -t vvanhees/ggir-default .
docker push vvanhees/ggir-default

# To use the docker images ggir-default
# update the command below to specify data folder, config.csv, and output folder
# add -d if you want to make it less verbose

docker run -it --rm --name ggir-defaut \
--mount type=bind,source="$(pwd)"/data,target=/data \
--mount type=bind,source="$(pwd)"/config.csv,target=/config.csv \
--mount type=bind,source="$(pwd)"/output,target=/output,bind-propagation=rslave \
  vvanhees/ggir-default
