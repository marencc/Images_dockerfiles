FROM ubuntu:xenial

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils \
    pkg-config build-essential zlib1g-dev libssl-dev \
    libssh2-1-dev libmariadb-client-lgpl-dev libxml2-dev libcurl4-gnutls-dev\
    wget software-properties-common libssl-dev curl \
    libcurl4-openssl-dev liblapack-dev libopenblas-base libopenblas-dev \
    gfortran libpng-dev libcairo2-dev libxml2-dev libfontconfig1-dev \
    libpq-dev libhdf5-dev git nano sqlite3 python python-biopython

RUN apt-get install gtkorphan
RUN gtkorphan

# get miniconda  ### NEED TO CONFIRM THE VERSION, I CANT SEEM TO SEE IT INSTALLED IN THE VM
# WORKDIR /root
# RUN wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
# RUN bash Miniconda2-latest-Linux-x86_64.sh -b && rm -f Miniconda2-latest-Linux-x86_64.sh

# Install R ## The installed version is R version 3.2.3 (2015-12-10) -- "Wooden Christmas-Tree"
RUN apt-get install r-base r-base-dev
RUN apt-get install -y --no-install-recommends r-base r-base-core r-cran-db r-cran-rmysql r-cran-rcurl
RUN R -e "install.packages('reticulate', dependencies=TRUE, repos='http://cran.rstudio.com/')"
RUN R -e "install.packages('Seurat', dependencies=TRUE, repos='http://cran.rstudio.com/')"
RUN R -e "install.packages('devtools', dependencies=TRUE, repos='http://cran.rstudio.com/')"

# get the Git repository
WORKDIR /root
RUN git clone https://github.com/BushmanLab/INSPIIRED
WORKDIR /root/INSPIIRED/bin/
RUN Rscript bin/setupINSPIIRED.R --noRsetup

## get blat 
WORKDIR /root
RUN wget https://users.soe.ucsc.edu/~kent/src/blatSrc35.zip
RUN unzip blatSrc35.zip
RUN cd blatSrc/
RUN 
