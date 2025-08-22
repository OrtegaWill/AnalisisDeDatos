#imagen base
FROM ubuntu:20.04
#Evita que el sistema operatvo retire instalaciones manuales
ENV DEBIAN_FRONTEND=noninteractive

#Se actualiza el sistema y se instalan los paquetes
RUN apt-get update && \
    apt-get install -y \
    python3 \
    python3-pip \
    python3-dev \
    build-essential \
    wget && \
    apt-get clean 

# Instalar Jupyter Notebook
RUN pip3 install jupyter

#Setear el espacio de trabajo
WORKDIR /workspace

RUN mkdir -p /root/.jupyter

#Configuraciones básicas para el Jupiter Notebook
RUN echo "c.NotebookApp.token = ''" > /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.password = ''" >> /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >> /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.allow_root = True" >> /root/.jupyter/jupyter_notebook_config.py

#Expone el puerto
EXPOSE 8888

#Comando por defecto para iniciar el contenedor
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]

 