FROM jupyter/tensorflow-notebook

RUN pip install jupyter_contrib_nbextensions
RUN pip install jupyter_nbextensions_configurator

RUN jupyter notebook --generate-config -y
RUN jupyter contrib nbextension install --user 
RUN jupyter nbextensions_configurator enable --user

# ENABLING EXTENSIONS - OOB 
RUN jupyter nbextension enable varInspector/main
RUN jupyter nbextension enable snippets/main
RUN jupyter nbextension enable snippets_menu/main
RUN jupyter nbextension enable table_beautifier/main
RUN jupyter nbextension enable toc2/main

# CONFIGURE THE CONFIG FILE WITH PROPER AWS CREDENTIALS 
# Allow for ENV variables for Superset Parameters 
ARG NOTEBOOK_PASSWORD

#Set the password
RUN sed -i "/c.NotebookApp.token*/c\c.NotebookApp.token = '$NOTEBOOK_PASSWORD'" $HOME/.jupyter/jupyter_notebook_config.py;

COPY requirements/requirements.txt requirements.txt
RUN pip install -r requirements.txt

