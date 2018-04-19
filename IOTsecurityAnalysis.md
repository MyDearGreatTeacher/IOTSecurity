# 系統架構

# 系統應用

[阿里云 · Elasticsearch](https://data.aliyun.com/product/elasticsearch?utm_content=se_1309736&gclid=Cj0KCQjw_ODWBRCTARIsAE2_EvWXzaSpLpM_EsKh8t-LvGNOoN6WQRHOpyFFCM0k01K4TzF4JXo7GT0aAo8YEALw_wcB)

# 本次實測環境

### 安裝 Java 8
```

```
### 安裝elastic search

```
[1]下載Download and unzip Elasticsearch

https://www.elastic.co/downloads

elasticsearch-6.2.2.zip

[2]解壓縮
將elasticsearch-6.2.2.zip解壓縮後改名為elasticsearch
放置D:\elasticsearch

[3]修改設定檔
修改 D:\elasticsearch\config\elasticsearch.yml
------------------------------
network.host: 0.0.0.0
------------------------------

[4]修改 bat檔 
Run bin/elasticsearch (or bin\elasticsearch.bat on Windows)

Run curl http://localhost:9200/ or Invoke-RestMethod http://localhost:9200 with PowerShell

D:\elasticsearch\bin\elasticsearch.bat

http://127.0.0.1:9200/

```
### 安裝 kibana

```
[1]下載

[2]解壓縮
將kibana-6.2.2-windows-x86_64.zip解壓縮後改名為kibana
放置D:\kibana

[3]修改設定檔
D:\kibana\config\kibana.yml
---------------------------------------
server.host: "0.0.0.0"
---------------------------------------
[4]修改 bat檔
C:\Program Files\kibana\bin\kibana.bat


http://127.0.0.1:5601/
```

### 安裝 winlogbeat

```
[1]下載
[2]解壓縮
將winlogbeat-6.2.2-windows-x86.zip解壓縮後改名為winlogbeat
放置D:\winlogbeat

[3]使用powershell安裝

Set-ExecutionPolicy RemoteSigned

cd 'C:\Program Files\Winlogbeat'
.\install-service-winlogbeat.ps1

[4]修改設定檔
D:\winlogbeat\winlogbeat.yml
修改如下:
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

[5]測試
.\winlogbeat.exe test config -c .\winlogbeat.yml -e


.\winlogbeat setup --template -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["localhost:9200"]'


http://localhost:9200/winlogbeat-*


.\winlogbeat setup --dashboards

[]使用powershell啟動winlogbeat服務

Start-Service winlogbeat
```

### ElasticSearch @ Ubuntu Linux 16.04 LTS(64-bit)

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

設定檔
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
