# APM on Docker

## Setup 

```bash
docker-compose up -d
```

* Após alguns minutos, o Kibana estará disponível na porta **5601**


## Configuração 

### Django

Instale as dependências:

```shell
pip install elastic-apm
```

Preencha as seguintes variáveis em `settings.py` : 

```python
# settings.py

INSTALLED_APPS = [
    'elasticapm.contrib.django',
    # outros aplicativos
]

ELASTIC_APM = {
    'SERVICE_NAME': 'my-app', 
    'SERVER_URL': 'http://apm-server:7200', # host e porta do apm-server
    'DEBUG': True, # True para monitorar o Django quando o debug_mode estiver ligado
}

MIDDLEWARE = [
    'elasticapm.contrib.django.middleware.TracingMiddleware',
    # outros middlewares
]

```
