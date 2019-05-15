# base image
FROM continuumio/miniconda3:latest
ADD ./app/environment.yml /

RUN set -x \
	&& mkdir /code

RUN apt-get update && \
    apt-get install -y unzip
# create the environment
RUN conda update -n base conda -y && conda env update

#RUN wget --no-check-certificate -O master.zip "https://github.com/nhm-usgs/onhm-fetcher-parser/archive/master.zip"
#RUN unzip -d /code master.zip
RUN curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | bash
RUN apt-get install git-lfs
RUN git lfs install

RUN cd code && \
    git clone https://github.com/nhm-usgs/onhm-fetcher-parser.git ofp
#RUN cd code && \
#    git pull
#RUN set -x \
#	&& cd code/onhm-fetcher-parser-master/pkg \
#	&& pwd
RUN cd code/ofp/pkg

CMD ["python", "./code/ofp/pkg/onhm_fp_script.py"]
# and remain running
CMD ["sleep", "infinity"]
