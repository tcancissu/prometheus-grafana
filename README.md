Stack Observability com Prometheus, Grafana e Alertmanager.

Aplicação Java com Spring Boot instrumentalizada para externalizar métricas com Actuador e exportar para o Prometheus usando o io.micrometer.
- Incluído as dependencias do Spring Actuator e do io.micrometer no Pom.xml.
- Configurado o actuator e o prometheus no aplication.properties.
- Instrumentalizado a aplicação com métricas personalizadas para auth_user_success e auth_user_error na classe AutenticacaoController.

Configurando o Prometheus
- Acesso: http://localhost:9090/
- Usando configurações padrões no arquivo prometheus/prometheus.yml

Configurando o Grafana
- Acesso: http://localhost:3000/ (senha padrão admin:admin)
- Configurado o data source prometheus, usando na url do host do container do prometheus no Docker.
- Criado um dashboard novo no Grafana e configurado diversas visualizações de métricas SRE 4 golden signals e dos métodos RED e USE. 

Configurando o Alertmanager
- Configurado 2 regras de alert no arquivo prometheus/alert.rules.
- Configurado o arquivo alert.rules tanto no arquivo de configurações do prometheus (prometheus/prometheus.yml) quanto nos volumes do prometheus no docker-compose.
- No Slack foi criado um canal e gerado um incoming-webhook. A url do webhook foi inserida no arquivo de configuração alertmanager/alertmanager.yml.


Para autenticação na API de teste
[POST] http://localhost/auth
{
    "email": "moderador@email.com",
    "senha": "123456"
}