FROM tensorflow/tensorflow:1.15.0-py3

COPY imloc.req.txt /tmp/
RUN pip install -r /tmp/imloc.req.txt

RUN useradd --create-home mluser
WORKDIR /home/mluser

RUN mkdir /share

USER mluser

# documentation of publishable port
EXPOSE 9999

CMD jupyter notebook --no-browser --ip 0.0.0.0 --port 9999 --NotebookApp.token='' --NotebookApp.password=''