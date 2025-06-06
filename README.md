# GS-Edge-Computing
Gustavo Garcia Silva RM: 562078
Gustavo Oliveira Barroso RM: 565705
Nicolas Santana Gará RM: 561461

**Contexto Simulado**

Diante dos recorrentes problemas causados por bueiros entupidos, desenvolvemos um sistema de drenagem de água e resíduos sólidos. Esse sistema conta com um sensor que, ao detectar o aumento do nível da água, aciona automaticamente um mecanismo de abertura de uma espécie de "alçapão", permitindo o escoamento da água acumulada. Dessa forma, o nível da água é reduzido, contribuindo para a prevenção de alagamentos.

Para o desenvolvimento desse sistema, utilizamos como referência o córrego da Tiquatira, localizado na zona leste de São Paulo. Esse córrego possui uma profundidade total de 16 metros, sendo que o nível considerado seguro da lâmina d'água, sem risco de enchente, é de aproximadamente 1,5 metro.

Com base nesses dados, propomos a instalação do sensor a 15 metros de altura. Quando o nível da água atingir 14,5 metros, o sensor ativará automaticamente o sistema, abrindo o "alçapão" e iniciando o processo de drenagem preventiva.

**Funcionamento do Sistema no Wokwi**

Para a criação deste sistema, utilizamos os seguintes componentes: Arduino UNO, servomotor e sensor ultrassônico HC-SR04.

O funcionamento ocorre da seguinte forma: quando a água atinge a distância de 50 cm do sensor (configuração que pode ser ajustada manualmente nas propriedades do sensor HC-SR04), o sistema é acionado automaticamente. Esse acionamento resulta na abertura do alçapão, representado no simulador pelo movimento do eixo móvel do servomotor.

**Código Fonte Wokwi**

#include <Servo.h>

const int trigPin = 9;
const int echoPin = 10;
const int limiar = 50; // cm
const int ledTriturador = 5; // LED do triturador
const int ledAlcapao = 6;    // LED indicador alçapão

Servo alcapao;

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledTriturador, OUTPUT);
  pinMode(ledAlcapao, OUTPUT);
  alcapao.attach(3);
  alcapao.write(0); // alçapão fechado
  digitalWrite(ledTriturador, LOW);
  digitalWrite(ledAlcapao, LOW);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  int distancia = duration * 0.034 / 2;

  Serial.print("Distância (cm): ");
  Serial.println(distancia);

  if (distancia <= limiar) {
    alcapao.write(90);
    digitalWrite(ledAlcapao, HIGH);
    digitalWrite(ledTriturador, HIGH);
    Serial.println("⚠️  Alçapão aberto - Nível crítico atingido!");
    Serial.println("🗑️ Triturador ligado!");
  } else {
    alcapao.write(0);
    digitalWrite(ledAlcapao, LOW);
    digitalWrite(ledTriturador, LOW);
    Serial.println("✅ Alçapão fechado - Nível normal.");
  }

  delay(1000);
}

**-----------------------------------------------------------------**

link Wokwi
https://wokwi.com/projects/432338099675104257

link Vídeo
https://youtu.be/1J_Guhyhk4A
