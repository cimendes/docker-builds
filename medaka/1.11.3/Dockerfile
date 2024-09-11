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

# medaka tools list_models
# Available: r103_fast_g507, r103_fast_snp_g507, r103_fast_variant_g507, r103_hac_g507, r103_hac_snp_g507, r103_hac_variant_g507, r103_min_high_g345, r103_min_high_g360, r103_prom_high_g360, r103_prom_snp_g3210, r103_prom_variant_g3210, r103_sup_g507, r103_sup_snp_g507, r103_sup_variant_g507, r1041_e82_260bps_fast_g632, r1041_e82_260bps_fast_variant_g632, r1041_e82_260bps_hac_g632, r1041_e82_260bps_hac_v4.0.0, r1041_e82_260bps_hac_v4.1.0, r1041_e82_260bps_hac_variant_g632, r1041_e82_260bps_hac_variant_v4.1.0, r1041_e82_260bps_sup_g632, r1041_e82_260bps_sup_v4.0.0, r1041_e82_260bps_sup_v4.1.0, r1041_e82_260bps_sup_variant_g632, r1041_e82_260bps_sup_variant_v4.1.0, r1041_e82_400bps_fast_g615, r1041_e82_400bps_fast_g632, r1041_e82_400bps_fast_variant_g615, r1041_e82_400bps_fast_variant_g632, r1041_e82_400bps_hac_g615, r1041_e82_400bps_hac_g632, r1041_e82_400bps_hac_v4.0.0, r1041_e82_400bps_hac_v4.1.0, r1041_e82_400bps_hac_v4.2.0, r1041_e82_400bps_hac_v4.3.0, r1041_e82_400bps_hac_variant_g615, r1041_e82_400bps_hac_variant_g632, r1041_e82_400bps_hac_variant_v4.1.0, r1041_e82_400bps_hac_variant_v4.2.0, r1041_e82_400bps_hac_variant_v4.3.0, r1041_e82_400bps_sup_g615, r1041_e82_400bps_sup_v4.0.0, r1041_e82_400bps_sup_v4.1.0, r1041_e82_400bps_sup_v4.2.0, r1041_e82_400bps_sup_v4.3.0, r1041_e82_400bps_sup_variant_g615, r1041_e82_400bps_sup_variant_v4.1.0, r1041_e82_400bps_sup_variant_v4.2.0, r1041_e82_400bps_sup_variant_v4.3.0, r104_e81_fast_g5015, r104_e81_fast_variant_g5015, r104_e81_hac_g5015, r104_e81_hac_variant_g5015, r104_e81_sup_g5015, r104_e81_sup_g610, r104_e81_sup_variant_g610, r10_min_high_g303, r10_min_high_g340, r941_e81_fast_g514, r941_e81_fast_variant_g514, r941_e81_hac_g514, r941_e81_hac_variant_g514, r941_e81_sup_g514, r941_e81_sup_variant_g514, r941_min_fast_g303, r941_min_fast_g507, r941_min_fast_snp_g507, r941_min_fast_variant_g507, r941_min_hac_g507, r941_min_hac_snp_g507, r941_min_hac_variant_g507, r941_min_high_g303, r941_min_high_g330, r941_min_high_g340_rle, r941_min_high_g344, r941_min_high_g351, r941_min_high_g360, r941_min_sup_g507, r941_min_sup_snp_g507, r941_min_sup_variant_g507, r941_prom_fast_g303, r941_prom_fast_g507, r941_prom_fast_snp_g507, r941_prom_fast_variant_g507, r941_prom_hac_g507, r941_prom_hac_snp_g507, r941_prom_hac_variant_g507, r941_prom_high_g303, r941_prom_high_g330, r941_prom_high_g344, r941_prom_high_g360, r941_prom_high_g4011, r941_prom_snp_g303, r941_prom_snp_g322, r941_prom_snp_g360, r941_prom_sup_g507, r941_prom_sup_snp_g507, r941_prom_sup_variant_g507, r941_prom_variant_g303, r941_prom_variant_g322, r941_prom_variant_g360, r941_sup_plant_g610, r941_sup_plant_variant_g610
# Default consensus:  r1041_e82_400bps_sup_v4.3.0
# Default variant:  r1041_e82_400bps_sup_variant_v4.3.0

# set the environment, add base conda/micromamba bin directory into path
# set locale settings to UTF-8
# set the environment, put new conda env in PATH by default
ENV PATH="/opt/conda/bin:${PATH}" \
  LC_ALL=C.UTF-8

# set final working directory to /data
WORKDIR /data
