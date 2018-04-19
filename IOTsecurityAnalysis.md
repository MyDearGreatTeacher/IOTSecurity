# 系統架構



# 安裝elastic search

```
將elasticsearch-6.2.2.zip解壓縮後改名為elasticsearch
放置C:\Program Files\elasticsearch

C:\Program Files\elasticsearch\config\elasticsearch.yml
------------------------------
network.host: 0.0.0.0
------------------------------

C:\Program Files\elasticsearch\bin\elasticsearch.bat

http://127.0.0.1:9200/
```
# 安裝 kibana

```
將kibana-6.2.2-windows-x86_64.zip解壓縮後改名為kibana
放置C:\Program Files\kibana


C:\Program Files\kibana\config\kibana.yml
---------------------------------------
server.host: "0.0.0.0"
---------------------------------------

C:\Program Files\kibana\bin\kibana.bat


http://127.0.0.1:5601/
```

# 安裝 winlogbeat

```
將winlogbeat-6.2.2-windows-x86.zip解壓縮後改名為winlogbeat
放置C:\Program Files\winlogbeat


Set-ExecutionPolicy RemoteSigned
cd 'C:\Program Files\Winlogbeat'
.\install-service-winlogbeat.ps1


C:\Program Files\winlogbeat\winlogbeat.yml
---------------------------------------
winlogbeat.event_logs:
  - name: Application
  - name: Security
  - name: System

output.elasticsearch:
  hosts:
    - localhost:9200

setup.kibana:
  host: "localhost:5601"
  
logging.to_files: true
logging.files:
  path: C:/ProgramData/winlogbeat/Logs
logging.level: info
---------------------------------------

.\winlogbeat.exe test config -c .\winlogbeat.yml -e


.\winlogbeat setup --template -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["localhost:9200"]'


http://localhost:9200/winlogbeat-*


.\winlogbeat setup --dashboards


Start-Service winlogbeat

```




```
sudo apt-get install openjdk-8-jre
sudo apt-get install grok
curl -L -O https://artifacts.elastic.co/downloads/logstash/logstash-5.2.0.zip
unzip logstash-5.2.0.zip
sudo mv logstash-5.2.0/ /opt
cd /opt 
sudo mv logstash-5.2.0/ logstash
```
```
sudo apt-get install ant texinfo openjdk-8-jdk build-essential
git clone https://github.com/jnr/jffi.git
cd jffi
ant jar
sudo cp build/jni/libjffi-1.2.so /opt/logstash/vendor/jruby/lib/jni/arm-Linux

sudo vim config/jvm.options
----------------------------------
-Xms512m
-Xmx512m
----------------------------------



cd /opt/logstash
sudo vim apache-filter.conf 


----------------------------------
input {
  file {
    path => "/var/log/apache2/access.log"
    start_position => "beginning"
  }
}

filter {
  if [path] =~ "access" {
    mutate { replace => { "type" => "apache_access" } }
    grok {
      match => { "message" => "%{COMBINEDAPACHELOG}" }
    }
  }
  date {
    match => [ "timestamp" , "dd/MMM/yyyy:HH:mm:ss Z" ]
  }
}

output {
  elasticsearch {
    hosts => ["192.168.2.62:9200"]
  }
  stdout { codec => rubydebug }
}
----------------------------------

sudo bin/logstash -f apache-filter.conf


http://192.168.2.62:9200/_search?q=DVWA


http://127.0.0.1:5601/
```
