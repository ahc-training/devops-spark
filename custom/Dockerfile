ARG BASE_IMG

FROM $BASE_IMG

USER 0

COPY custom/pom.xml ./pom.xml
COPY custom/requirements.txt ./requirements.txt

RUN apt-get update && \
    apt-get install -y maven cmake

RUN mvn dependency:copy-dependencies '-DoutputDirectory=/opt/spark/jars'

RUN pip3 install --no-cache-dir --upgrade pip && \
    pip3 install --no-cache-dir -r requirements.txt

ARG spark_uid=185
USER ${spark_uid}
