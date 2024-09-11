FROM condaforge/miniforge3:23.3.1-1

ARG medakaVer=1.11.3

LABEL base.image="condaforge/miniforge3:23.3.1-1"
LABEL container.version="1"
LABEL software="Medaka"
LABEL software.version=${medakaVer}
LABEL description="Consensus sequence correction provided by ONT Research"
LABEL website="https://github.com/nanoporetech/medaka"
LABEL license="https://github.com/nanoporetech/medaka/blob/master/LICENSE.md"
LABEL maintainer1="Curtis Kapsak"
LABEL maintainer.email1="pjx8@cdc.gov"
LABEL maintainer2="Ines Mendes"
LABEL maintainer.email2="ines.mendes@theiagen.com"

# install dependencies; cleanup apt garbage
RUN apt-get update && apt-get install -y --no-install-recommends \
  wget \
  ca-certificates \
  git \
  libtiff5 \
  unzip \
  bsdmainutils \
  gcc && \
  apt-get autoclean && \
  rm -rf /var/lib/apt/lists/*

RUN mamba install -y --name base -c conda-forge -c bioconda \
  'bioconda::medaka==1.11.3' && \
  mamba clean -a -y

# set the environment, add base conda/micromamba bin directory into path
# set locale settings to UTF-8
# set the environment, put new conda env in PATH by default
ENV PATH="/opt/conda/bin:${PATH}" \
  LC_ALL=C.UTF-8

# set final working directory to /data
WORKDIR /data
