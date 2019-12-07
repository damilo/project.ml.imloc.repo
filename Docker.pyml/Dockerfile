FROM python:3.7.4-slim-buster

COPY pyml.requirements.txt /tmp/
RUN pip install -r /tmp/pyml.requirements.txt

COPY pycv.requirements.txt /tmp/
RUN pip install -r /tmp/pycv.requirements.txt

COPY imloc.req.txt /tmp/
RUN pip install -r /tmp/imloc.req.txt

RUN useradd --create-home mluser
WORKDIR /home/mluser

RUN mkdir /share

USER mluser

# documentation of publishable port
EXPOSE 9999

CMD jupyter notebook --no-browser --ip 0.0.0.0 --port 9999 --NotebookApp.token='' --NotebookApp.password=''