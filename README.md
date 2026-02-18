# Observability Instrumentation

**Visão Geral:** Projeto de exemplo contendo uma stack de observability com OpenTelemetry, Prometheus e Tempo, orquestrada por Docker Compose.

**Arquitetura:**
- **Collector:** Recebe métricas e traces via OpenTelemetry e exporta para os backends configurados.
- **Prometheus:** Coleta métricas expostas pelos serviços.
- **Tempo:** Armazena traces distribuídos para investigação e correlação.
- **Orquestração:** Todos os serviços são definidos em `docker-compose.yml` para execução local.

**Arquivos Principais:**
- **Compose:** [docker-compose.yml](docker-compose.yml) — define os serviços e volumes.
- **OTel Collector config:** [otel-collector-config.yaml](otel-collector-config.yaml) — configuração do Collector.
- **Prometheus config:** [prometheus.yml](prometheus.yml) — jobs e regras de scraping.
- **Tempo config:** [tempo.yml](tempo.yml) — configuração do Tempo (tracing backend).

**Requisitos:**
- **Docker:** versão compatível com `docker compose`.
- **Rede local:** portas expostas conforme definido em [docker-compose.yml](docker-compose.yml).

**Como executar (exemplo rápido):**
1. Subir a stack em modo destacado:

```bash
docker compose up -d
```

2. Acompanhar logs de um serviço (ex.: collector):

```bash
docker compose logs -f otel-collector
```

3. Parar e remover containers:

```bash
docker compose down
```

**Observações úteis:**
- **Ver configurações e portas:** consulte [docker-compose.yml](docker-compose.yml) para ver as portas expostas e mapeamentos.
- **Gerar tráfego de teste:** para validar métricas e traces, gere requisições contra suas aplicações instrumentadas apontando para o Collector.
- **Depuração:** use os logs do Collector e do Prometheus para diagnosticar scraping e exportação.

**Contribuição:**
- **Como contribuir:** abra uma issue descrevendo a sugestão ou um PR com mudanças pequenas e documentadas.

**Licença:**
- Arquivo sem licença especificada — adicione `LICENSE` conforme necessário.

--
Arquivo gerado automaticamente para facilitar execução e exploração local da stack de observability.
