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
    git clone --depth=1 https://github.com/nhm-usgs/onhm-fetcher-parser.git ofp \
    && cd ofp \
    && rm -rf .git \
    && pwd

#RUN git clone https://github.com/nhm-usgs/nhm_hru_shapefiles.git code/ofp/Data
RUN cd code/ofp && \
    wget -m -nH --cut-dirs=5 --user='anonymous' ftp://ftpext.usgs.gov/pub/cr/co/lakewood/nhm_hru_shp

WORKDIR /code/ofp/pkg

#CMD ["python", "onhm_fp_script.py"]
ENTRYPOINT["python", "onhm_fp_script.py"]
# and remain running
#CMD ["sleep", "infinity"]