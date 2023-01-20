# oxidized_exporter

A basic exporter to expose the status of the last backup.
This was written out of frustration, but it works and does the job

## Installation
```
cd /opt/
git clone https://github.com/momorientes/oxidized_exporter.git
cd oxidized_exporter
cp oxidized.conf.sample oxidized.conf
vim oxidized.conf #modify as needed
virtualenv -p python3 venv
source venv/bin/activate
pip install -r requirements.txt
./oxidized_exporter
```

## SystemD Service
copy the following to `/etc/systemd/system/oxidized_exporter.service`.  
Issue `systemctl daemon-reload && systemctl enable oxidized_exporter && systemctl start oxidized_exporter`.

```
[Unit]
Description=Prometheus oxidized Exporter 

[Service]
User=prometheus
Group=prometheus
ExecStart=/opt/oxidized_exporter/venv/bin/python3 oxidized_exporter
WorkingDirectory=/opt/oxidized_exporter

[Install]
WantedBy=multi-user.target
```
