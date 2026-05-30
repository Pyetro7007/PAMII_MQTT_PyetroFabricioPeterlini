# Dominando IoT com MQTT, ESP32 e React Native
 
Esse repositório compartilha um aplicativo mobile de IoT (Internet das Coisas), desenvolvido em JavaScript utilizando React Native com Expo. O projeto abrange duas etapas: a configuração do protocolo de comunicação MQTT via HiveMQ Cloud (Broker) e o desenvolvimento de um dashboard mobile capaz de publicar e assinar tópicos MQTT em tempo real. O foco está na comunicação segura com o Broker na nuvem, no controle simulado de uma lâmpada e na exibição de dados de sensores por meio de medidores circulares.
 
As tecnologias usadas foram:
 
- JavaScript
- React Native
- Expo
- MQTT (protocolo Pub/Sub)
- HiveMQ Cloud (Broker)
- react_native_mqtt
- react-native-circular-progress-indicator
- react-native-dotenv
---
 
## Pré-requisitos
 
- Node.js instalado no computador
- Conta gratuita no [HiveMQ Cloud](https://www.hivemq.com/mqtt-cloud-broker/)
- Aplicativo **Expo Go** instalado no celular
---
 
## Configurando o Broker (HiveMQ Cloud)
 
1. Acesse [hivemq.com/mqtt-cloud-broker](https://www.hivemq.com/mqtt-cloud-broker/) e crie uma conta gratuita.
2. Crie um novo cluster (opção Free Tier) e aguarde a ativação.
3. Na aba **Access Management**, crie um usuário e senha (ex: `aluno_etec` / `senha123`).
4. Anote o **Cluster URL** (ex: `xxxxxxxx.s1.eu.hivemq.cloud`) e a porta **8884** (WebSocket seguro).
---
 
## Configurando o Aplicativo Mobile
 
### Clonando o repositório
 
```
git https://github.com/Pyetro7007/PAMII_MQTT_PyetroFabricioPeterlini.git
```
 
### Acessando a pasta do projeto
 
```
cd PAMII_MQTT_PyetroFabricioPeterlini
```
 
### Instalando as dependências
 
```
npm install
```
 
Ou instale individualmente via Expo:
 
```
npx expo install react_native_mqtt @react-native-async-storage/async-storage
npx expo install react-native-vector-icons react-native-svg
npx expo install react-native-circular-progress-indicator
npx expo install react-native-dotenv
```
 
### Configurando as variáveis de ambiente
 
Crie um arquivo `.env` na raiz do projeto com suas credenciais reais:
 
```
MQTT_HOST=xxxxxxxx.s1.eu.hivemq.cloud
MQTT_PORT=8884
MQTT_PATH=/mqtt
MQTT_USER=seu_usuario
MQTT_PASS=sua_senha
```
 
> **Atenção:** O arquivo `.env` nunca deve ser enviado ao repositório. Adicione-o ao `.gitignore`. Use o arquivo `.env.example` como modelo para outros desenvolvedores.
 
### Executando o aplicativo
 
```
npx expo start --tunnel
```
 
Após executar o comando, será exibido um QR Code. Leia-o com o aplicativo **Expo Go** no celular.
 

 
## Tópicos MQTT utilizados
 
| Tópico      | Direção            | Descrição                      |
|-------------|--------------------|--------------------------------|
| `casa/luz`  | App → Broker       | Liga (1) ou desliga (0) a luz  |
| `casa/temp` | Broker → App       | Recebe a temperatura em °C     |
| `casa/umid` | Broker → App       | Recebe a umidade relativa em % |

