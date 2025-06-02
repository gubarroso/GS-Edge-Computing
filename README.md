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

link Wokwi
https://wokwi.com/projects/432338099675104257

link Vídeo
...
