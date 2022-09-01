# .
# ├── Dockerfile
# └── src
#     ├── requirements.txt
#     └── app.py
FROM python:3.10-alpine
RUN adduser -D gurterngrkrphgbe
USER gurterngrkrphgbe
WORKDIR ~
COPY src .
RUN pip install --no-cache-dir -r ./requirements.txt
CMD python3 ./app.py
