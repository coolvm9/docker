# Elastic Kibana Docker Images


## commands
Create network

% docker network create elastic


docker run \
        --name elasticsearch \
        --net elastic \
        -p 9200:9200 \
        -e discovery.type=single-node \
        -e ES_JAVA_OPTS="-Xms4g -Xmx4g"\
        -e xpack.security.enabled=false \
        -it \
        docker.elastic.co/elasticsearch/elasticsearch:8.9.0

docker run \
    --name elasticsearch \
    --net elastic \
    -p 9200:9200 \
    -e discovery.type=single-node \
    -e ES_JAVA_OPTS="-Xms4g -Xmx4g"\
    -e xpack.security.enabled=false \
    -it \
    docker.elastic.co/elasticsearch/elasticsearch:8.10.2


localhost:9200

docker run \
    --name kibana \
    --net elastic \
    -p 5601:5601 \
    docker.elastic.co/kibana/kibana:8.9.0

docker run \
    --name kibana \
    --net elastic \
    -p 5601:5601 \
    docker.elastic.co/kibana/kibana:8.10.2

pip3 install --upgrade pip
python -m pip install eland
eland_import_hub_model \
    --url http://localhost:9200/ \
    --hub-model-id sentence-transformers/msmarco-MiniLM-L-12-v3 \
    --task-type text_embedding \
    --start

docker run -it --rm --network elastic elastic/eland.

eland_import_hub_model \
--url https://<user>:<password>@localhost:9200/ \
--hub-model-id sentence-transformers/msmarco-MiniLM-L-12-v3 \
--task-type text_embedding \
--start

eland_import_hub_model \
    --url http://172.18.0.2:9200/ \
    --hub-model-id elastic/distilbert-base-cased-finetuned-conll03-english \
    --task-type ner \
    --start


eland_import_hub_model \
    --url http://172.18.0.2:9200/ \
    -u elastic -p password \
    --clear-previous \
    --hub-model-id sentence-transformers/msmarco-MiniLM-L-12-v3 \
    --task-type text_embedding \
    --start

eland_import_hub_model \
    --url http://172.18.0.2:9200/ \
    --clear-previous \
    --hub-model-id sentence-transformers/msmarco-MiniLM-L-12-v3 \
    --task-type text_embedding \
    --start



eland_import_hub_model \
    --url http://172.18.0.2:9200/ -u elastic -p password \
    --hub-model-id sentence-transformers/msmarco-MiniLM-L-12-v3 \
    --task-type text_embedding \
    --start
POST _ml/trained_models/sentence-transformers__msmarco-minilm-l-12-v3/deployment/_start

https://www.elastic.co/blog/how-to-deploy-nlp-sentiment-analysis-example


eland_import_hub_model \
    --url http://172.18.0.2:9200/ \
    --hub-model-id distilbert-base-uncased-finetuned-sst-2-english \
    --task-type text_classification \
    --start
### Notes

### References
https://levelup.gitconnected.com/how-to-run-elasticsearch-8-on-docker-for-local-development-401fd3fff829
https://mohaamer5.medium.com/logstash-for-synchronize-elasticsearch-with-dbs-e5dda7cea930

Since the --start option is used at the end of the Eland import command, Elasticsearch deploys the model ready to use. If you have multiple models and want to select which model to deploy, you can use the Machine Learning > Model Management user interface in Kibana to manage the starting and stopping of models.

Go to the Machine Learning > Trained Models page and synchronize your trained models. A warning message is displayed at the top of the page that says "ML job and trained model synchronization required". Follow the link to "Synchronize your jobs and trained models." Then click Synchronize. You can also wait for the automatic synchronization that occurs in every hour, or use the sync machine learning objects API.

