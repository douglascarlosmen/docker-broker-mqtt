# Broker MQTT com Mosquitto e Docker Compose

Este projeto configura um broker MQTT utilizando o Mosquitto em um ambiente Docker, com autenticação de usuário para garantir uma comunicação segura.

## Funcionalidades

- Broker MQTT Mosquitto rodando em um container Docker.
- Autenticação de usuário para conectar ao broker MQTT.
- Persistência de dados para garantir a durabilidade das mensagens.
- Configuração simples e rápida através do Docker Compose.

## Pré-requisitos

Antes de iniciar, certifique-se de que você tem o Docker, Docker Compose e o Mosquitto instalados em sua máquina. Estas ferramentas são necessárias para construir e rodar o container do Mosquitto.

## Configuração

O projeto utiliza o Docker Compose para simplificar a configuração e a execução do broker MQTT Mosquitto.

**1. Clonar o Repositório**

   Primeiro, clone este repositório para obter os arquivos de configuração necessários:

   ```bash
   git clone https://github.com/douglascarlosmen/docker-broker-mqtt.git
   cd docker-broker-mqtt
   ```

**2. Configurar Credenciais**

Para adicionar autenticação ao broker MQTT, você precisa criar um arquivo de senha e configurar as credenciais dos usuários que terão permissão para se conectar ao broker.

a. Execute o seguinte comando para gerar o arquivo de senha com um usuário:

```bash
mosquitto_passwd -c mosquitto/config/mosquitto_passwd seu_usuario
```

b. Quando solicitado, insira a senha desejada para o usuário seu_usuario. Este usuário será utilizado para autenticar no broker MQT

**3. Arquivo de Configuração do Mosquitto**

Edite o arquivo `mosquitto/config/mosquitto.conf` para incluir as seguintes linhas, assegurando que o broker utilize o arquivo de senha para autenticação:

```conf
allow_anonymous false
password_file /mosquitto/config/mosquitto_passwd
listener 1883
```

**4. Iniciar o Broker MQTT**

Com a configuração completa, utilize o Docker Compose para iniciar o broker MQTT:

```bash
docker-compose up -d
```