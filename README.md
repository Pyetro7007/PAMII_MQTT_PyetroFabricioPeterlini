# Dominando IoT com MQTT, ESP32 e React Native
 
Esse repositório compartilha um aplicativo mobile de IoT, desenvolvido em JavaScript utilizando React Native com Expo. O projeto abrange a configuração do protocolo MQTT via HiveMQ Cloud e o desenvolvimento de um dashboard mobile para publicar e assinar tópicos em tempo real. O app inclui persistência de dados local para histórico de leituras.
 
As tecnologias usadas foram:
 
- JavaScript
- React Native
- Expo
- MQTT (protocolo Pub/Sub)
- HiveMQ Cloud (Broker)
- Async Storage (para histórico local)
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
git clone https://github.com/Pyetro7007/PAMII_MQTT_PyetroFabricioPeterlini.git
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

### Armazenamento Local

O app salva automaticamente o histórico de leituras (temperatura e umidade) no dispositivo utilizando AsyncStorage com a chave @sensor_history, garantindo que os dados não sejam perdidos ao fechar o aplicativo.
 
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
npx expo start
```
 
Após executar o comando, será exibido um QR Code. Leia-o com o aplicativo **Expo Go** no celular.
 

 
## Tópicos MQTT utilizados
 
| Tópico      | Direção            | Descrição                      |
|-------------|--------------------|--------------------------------|
| `casa/luz`  | App → Broker       | Liga (1) ou desliga (0) a luz  |
| `casa/temp` | Broker → App       | Recebe a temperatura em °C     |
| `casa/umid` | Broker → App       | Recebe a umidade relativa em % |

Vídeo informativo: https://youtu.be/KF1vaqmT4Qw

