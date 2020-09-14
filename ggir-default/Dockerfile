## Base image https://hub.docker.com/u/vvanhees/
## This has R and GGIR
FROM vvanhees/base-r-ggir:latest

RUN mkdir -p /data
RUN mkdir -p /code
RUN mkdir -p /output

COPY /code/runGGIR.R /code/runGGIR.R

## run the script
CMD Rscript /code/runGGIR.R
