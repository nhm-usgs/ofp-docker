# base image
FROM continuumio/miniconda3:latest
ADD ./app/environment.yml /

RUN apt-get update && \
    apt-get install -y unzip
# create the environment
RUN conda update -n base conda -y && conda env update

RUN wget --no-check-certificate -O master.zip "https://github.com/nhm-usgs/onhm-fetcher-parser/archive/master.zip"
RUN unzip -d /code master.zip

CMD ["python", "code/onhm-fetcher-parser-master/pkg/ohnm_fp_script.py"]
# and remain running
#CMD ["sleep", "infinity"]
