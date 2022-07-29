# Fork from a minimal conda/jupyter Python3 environment.
# https://hub.docker.com/r/jupyter/minimal-notebook/tags
FROM jupyter/minimal-notebook:57ebe55c07d0

ARG JUPYTERHUB_VERSION=2.3.1

MAINTAINER Iris Christadler & Tobias Megies <megies@geophysik.uni-muenchen.de>

# Install system libs as root.
# Git is already contained in the minimal-notebook
# TODO do we need gfortran?
#USER root
#RUN apt update
#RUN apt install -y gfortran 

# Rest as jovyan user who is provided by the Jupyter notebook template.
USER jovyan

# add conda-forge channel and move it to top of channel list
# conda-forge is already in the list
RUN conda config --add channels conda-forge && conda config --add channels conda-forge

# Install ObsPy and other packages
RUN conda install --yes 'obspy=1.3.0' 
RUN conda install --yes cartopy 
RUN conda install --yes nbgitpuller 
RUN conda install --yes pandas seaborn sqlalchemy 
#RUN conda install --yes instaseis

RUN pip3 install --no-cache jupyterhub==$JUPYTERHUB_VERSION
RUN pip3 install --no-cache pytest pytest-json-report


# Install the rate and state toolkit.
# TODO Necessary?
#RUN pip install https://github.com/jrleeman/rsfmodel/archive/master.zip

# Install the jupyter dashboards.
RUN pip install jupyter_dashboards && \
  jupyter dashboards quick-setup --sys-prefix && \
  jupyter nbextension enable jupyter_dashboards --py --sys-prefix

# Install the code folding plugin.
RUN conda install --yes -c conda-forge jupyter_contrib_nbextensions && \
  jupyter contrib nbextension install --user && \
  jupyter nbextension enable codefolding/main

# Clone seismo-live git repo (will be updated in the Dockerfile run by binder)
# n.b. currently it will *not* be updated, but used as is in the state that is
# checked out here
#XXX RUN git clone https://github.com/krischer/seismo_live.git /home/jovyan/seismo_live
#RUN git clone https://github.com/krischer/seismo_live_build.git /home/jovyan/seismo_live
#RUN rm -rf /home/jovyan/work; mv /home/jovyan/seismo_live/notebooks/* /home/jovyan/; rm -rf /home/jovyan/seismo_live

# IRIS 
#RUN git clone should be replaced by COPY
# So I put a copy of seismo_live/notebooks in the Dockerfile directory
ADD notebooks /home/jovyan/
RUN rm -rf /home/jovyan/work

# A bit ugly but unfortunately necessary: https://github.com/docker/docker/issues/6119
USER root
RUN chown -R jovyan:users /home/jovyan
USER jovyan

# This might exist locally and will thus be copied to the docker image...
# Iris: This directory does not exist (anymore?)
#RUN rm -rf /home/jovyan/Instaseis-Syngine/data/database
# XXX # Instaseis download deactivated since we don't install it right now, see above
# XXX # Download the instaseis database.
# XXX RUN mkdir -p /home/jovyan/Instaseis-Syngine/data/database
# XXX RUN wget -qO- "http://www.geophysik.uni-muenchen.de/~krischer/instaseis/20s_PREM_ANI_FORCES.tar.gz" | tar xvz -C /home/jovyan/Instaseis-Syngine/data/database

# Set a default backend for matplotlib!
RUN mkdir -p ~/.config/matplotlib && touch ~/.config/matplotlib/matplotlibrc && printf "\nbackend: nbagg\n" >> ~/.config/matplotlib/matplotlibrc

# Build the font cache so its already done in the notebooks.
RUN python -c "from matplotlib.font_manager import FontManager; FontManager()"

# XXX ugly hack to try and work around proj env issues
# XXX https://github.com/conda-forge/basemap-feedstock/issues/30
ENV PROJ_LIB=/opt/conda/share/proj/

# Test and report, for now continue even if errors are reported
# XXX RUN obspy-runtests --all --no-flake8 -r -n seismo-live-baseimage || true
# XXX for now don't run network tests, because it takes quite a while
# Iris: Omit tests, only run them in the image
# Iris: Should only be obspy-runtests (no arguments)
#RUN obspy-runtests --no-flake8 -r -n seismo-live-baseimage || true

# Ignore all Python warnings because they look ugly in the docs.
# Iris: I am curious to see, whether cartopy needs to download the maps only once
#ENV PYTHONWARNINGS ignore
