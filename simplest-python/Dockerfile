# .
# ├── Dockerfile
# └── src
#     ├── requirements.txt
#     └── app.py
FROM python:3.10-slim-bullseye
WORKDIR /root/app/
COPY src .
RUN pip install --disable-pip-version-check --no-cache-dir -r ./requirements.txt
CMD python3 ./app.py
