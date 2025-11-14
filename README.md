# ESPK1
# Márcio Alexnadre 566238
# Fabio Apolinario 561828
# Leonardo Lopes 562171

# Tema principal do projeto: TI verde e sustentabilidade

O problema que é abordado e solucionado é  a administração de hortaliças, onde muitas não tem sistemas que monitaram fatores ambientais como a temperatura e humidade locais, que são fatores importantíssimos para o desenvolvimento de vegetais, 
além do uso despreocupado de irrigadores d'agua os quais passam mais de 1 hora irrigando hortas gastando litros d'agua, o que não é um problema, mas e se não tivesse uma necessecidade de irrigar plantas? Por exemplo, se chovesse teria mesmo a necessidade de molhas a plantas assim tornando o 
solo que já está molhado e úmido em lama? Por isso o sistema que foi criado tem um relógio próprio o qual todo dia às 6 horas, o sistema verifica a humidade local e se tem mesmo necessidade de irrigar o local, se sim, o sistema ficará por um tempo irrigando o solo
e logo depois irá parar, o sistema foi feito de forma simples, mas também poderíamos adicionar um tempo fixo de duração da irrigação, como uma hora.

# Sobre o sistema:
O sistema princípal é baseado em 5 itens: Um sensor DHT, um relógio RTC, leds coloridos, um piezo/buzzer e um micro-controlador ESP32

<img width="856" height="539" alt="image" src="https://github.com/user-attachments/assets/ebc9a0c4-ea67-48f6-8026-00c73d108b17" />

Como o sistema PRINCIPAL funciona: Primeiramente o sistema tenta se conectar à internet para que sejam feita as conexões MQTT ou HTTP, se ele não conectar, ele não irá funcionar e irá ficar tentando se reconectar o tempo inteiro, logo após a conexão, o sistema irá começar 
a fazer a leitura da temperatura e humidade, e depois checará se o RTC está ou não conectado, se ele não estiver, o sistema não vai fazer a leitura do tempo e o led amarelo irá ficar acesso para dizer que está com problema, agora caso esteja conectado 
o sistema verá se são 6 da manhã e se a humidade está abaixo de 90%, caso esteja tudo correto, o sistema irá ligar o sistema de irrigadores (o qual o led verde está sendo usado como decoy), o led vermelho e o piezo para avisar que os irrigadores estão ligados 
logo após esse processo, o sistema irá salvar todas as informações pegas e irão mandar à nuvem onde serão registradas.

O que impacta: Menor gasto desnecessário de água no planeta, além do monitoramento de sáude de plantas para que tenham a melhor qualidade possível, trazendo mais saúde às pessoas.

# Sobre como o MQTT funciona

![bevyblog96_banner](https://github.com/user-attachments/assets/1a921cbe-c7d2-4484-9a31-3c9756969bc9)

O protocolo MQTT funciona da seguinte forma: O dispositivo IOT (ESP32 e outros) reune e pública informações na núvem MQTT, essas informações logo serão processadas sobre um IP público ou privado sobre uma porta em específico, logo depois as informações públidas após o processor da núvem são registradas em seus devídos tópicos.
O sistema MQTT pode ser mais utilizado para empresas de grandes ramos, as quais tem muitos estabelecimentos e necessitam de um monitoramento em massa, como monitoramento da velocidade de carros para saber e registrar placas de pessoas que estão acima do limite de velocidade.

Tópicos: O  nosso sistema utiliza apenas 3 tópicos, sendo eles o de humidade, temperatura e irrigação (Se os irrigadores estão ou não ligados).

# ThingSpeak:

<img width="932" height="829" alt="image" src="https://github.com/user-attachments/assets/067430c2-de6c-499c-ad5e-8453f588b1d6" />
O ThingSpeak tem um sistema e protocolo semelhante ao MQTT, com a diferença de ser menos complicado e mais simples de se manusear e monitorar já que ele automaticamente cria um dashboard,  
é mais sugerido para que o ThingSpeak seja utilizado em empresas mais simples e pequenas, já que ele foi feito mais para pequenas coisas e pode registrar apenas valores matemáticos, como lojas pequenas monitorando a entrada e a saída de dinheiro em caixas ou monitoramento de casas para ver se tem algum movimento em suas casas 
por questão de segurança.
