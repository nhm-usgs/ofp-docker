# base image
FROM continuumio/miniconda3:latest
ADD ./app/environment.yml /

# create the environment
RUN conda update -n base conda -y && conda env update


# and remain running
CMD ["sleep", "infinity"]
