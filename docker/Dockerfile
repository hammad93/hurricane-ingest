FROM continuumio/anaconda3:2020.07

# database credentials
COPY credentials.csv /root/

# Python additional requirements
COPY requirements.txt /root/
RUN pip install -r /root/requirements.txt

# Add git repository
RUN git clone --single-branch --branch main https://github.com/hammad93/hurricane-ingest.git

# Setup cron job
RUN apt-get --allow-releaseinfo-change update && apt-get -y install cron
RUN apt-get install -y gnupg2

# Entrypoint
ADD entrypoint.sh /root/entrypoint.sh
RUN chmod +x /root/entrypoint.sh
ENTRYPOINT /root/entrypoint.sh
