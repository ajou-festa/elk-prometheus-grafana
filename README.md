# 기본 명령어

```
docker-compose up -d
```

```
docker-compose down -v
```


# 주의 사항
그라파나에서 프로메테우스로의 앤드포인트 설정할 때, `localhost` 말고 <strong>`host.docker.internal`</strong>를 입력해야됨

kibana 뜨는 게 좀 느림 그리고 가끔씩 elasticsearch가 잘 작동하지 않는 경우가 있음

프로메테우스에서 spring로 특정 앤드포인트를 찌름
```yaml
scrape_configs:
  - job_name: 'festi'
    metrics_path: '/actuator/prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['host.docker.internal:8080']
```
해당 metrics_path가 default path에 따라서 달라짐 즉 default를 api로 정해논 상황이라면, `/api/actuator/prometheus` 로 수정

