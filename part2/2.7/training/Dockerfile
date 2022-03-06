FROM python:3.6.7-slim

WORKDIR /src

COPY . .

RUN apt-get update
RUN apt-get install ffmpeg libsm6 libxext6 -y

RUN pip install --upgrade pip
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip install -r requirements.txt

CMD ["python", "-u", "train.py"]
