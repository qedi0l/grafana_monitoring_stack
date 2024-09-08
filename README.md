# ОПИСАНИЕ ПРОЕКТА

Бандл для мониторинга серверов на базе `Grafana` и `Prometheus`. Вспомогательные иструменты `grafana-image-renderer`, `pushgateway`, `node-exporter`.

Настроен для работы только с `docker-compose`


<details>
<summary>Нюансы работы:</summary>

- Для хранения данных указаны относительные пути в каталог с docker-compose файлом
- Версии Grafana и Prometheuы указаны latest, при необходимости замените их на нужные вам.
- Для мониторинга приложения необходимо чтобы в его окружении работал node-exporter, а так же в файле config/proetheus.yaml указать эту новую ноду.
- Для получения метрик от докера необходимо добавить в конфигурацию docker engine строку ` "metrics-addr": "localhost:9323" `

</details>
<br>
Установка и настройка:

1. Склонируйте репозиторий.
2. Запустите команду:
`sudo mkdir -p ./grafana/config && \
sudo mkdir -p ./grafana/{grafana-config,grafana-data,prometheus-data} && \
sudo chown -R $(id -u):$(id -g) {./grafana/config,./grafana} && \
touch ./grafana/grafana-config/grafana.ini && \
cp config/* ./grafana/config/ && \
docker compose up -d`
3. Установить новые пароль в конфигурационных файлах
4. перейти по адресу 127.0.0.1:3000 (grafana) и установить новый пароль.