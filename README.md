# Projeto: Cancela Automática com ESP32

## 📌 Descrição

Este projeto foi desenvolvido utilizando um **ESP32**, um sensor ultrassônico, um servo motor e um LED para simular o funcionamento de uma cancela automática de estacionamento.

O sistema detecta a distância de um objeto, como um carro, em relação ao sensor ultrassônico. Quando o objeto está a uma distância menor ou igual a **50 centímetros**, o LED acende e a cancela é aberta. Quando o objeto se afasta, o LED apaga e a cancela retorna à posição fechada.

## 🎯 Objetivo

Desenvolver um sistema automatizado de controle de entrada em um estacionamento, utilizando um sensor ultrassônico para detectar a aproximação de veículos e um servo motor para movimentar a cancela.

## 🛠️ Tecnologias e componentes utilizados

* **ESP32:** Microcontrolador responsável por executar o código e controlar os componentes.
* **C++:** Linguagem de programação utilizada no desenvolvimento do projeto.
* **Sensor ultrassônico:** Mede a distância entre o sensor e o objeto detectado.
* **Servo motor:** Responsável por abrir e fechar a cancela.
* **LED:** Indica quando a cancela está aberta.
* **Monitor Serial:** Exibe a distância medida pelo sensor em centímetros.
* **Biblioteca ESP32Servo:** Permite controlar o servo motor utilizando o ESP32.

## 🔌 Ligações dos componentes

| Componente                  | Pino do ESP32 |
| --------------------------- | ------------- |
| TRIG do sensor ultrassônico | GPIO 5        |
| ECHO do sensor ultrassônico | GPIO 18       |
| Servo motor                 | GPIO 13       |
| LED                         | GPIO 4        |

## ⚙️ Funcionamento do sistema

1. O ESP32 envia um pulso ultrassônico pelo pino TRIG.
2. O sensor recebe o eco desse pulso pelo pino ECHO.
3. O programa calcula a distância do objeto em centímetros.
4. A distância é exibida no Monitor Serial.
5. Se o objeto estiver a até 50 cm do sensor, o LED acende e o servo motor gira para 90°, abrindo a cancela.
6. Se o objeto estiver a mais de 50 cm ou não for detectado, o LED apaga e o servo retorna a 0°, fechando a cancela.
7. O sistema repete esse processo continuamente.

## 📏 Regra de funcionamento

| Distância do objeto                  | LED       | Cancela      |
| ------------------------------------ | --------- | ------------ |
| Menor ou igual a 50 cm e maior que 0 | Ligado    | Aberta — 90° |
| Maior que 50 cm                      | Desligado | Fechada — 0° |
| Igual a 0 cm                         | Desligado | Fechada — 0° |

## 💻 Código-fonte

O código principal utiliza a biblioteca `ESP32Servo.h` para controlar o servo motor e a função `pulseIn()` para medir o tempo de retorno do sinal ultrassônico.

A distância é calculada pela seguinte fórmula:

```cpp
float distancia = tempo * 0.034 / 2;
```

O valor `0.034` representa aproximadamente a velocidade do som em centímetros por microssegundo. A divisão por 2 ocorre porque o sinal percorre o caminho até o objeto e retorna ao sensor.

## ▶️ Como executar o projeto

1. Abra o código no Arduino IDE ou em um simulador compatível, como o Wokwi.
2. Instale a biblioteca **ESP32Servo**.
3. Monte as ligações conforme a tabela de componentes.
4. Carregue o código no ESP32.
5. Abra o Monitor Serial e configure a velocidade para **115200 baud**.
6. Aproxime um objeto do sensor e observe o funcionamento do LED e da cancela.

## 📚 Aprendizados

Com este projeto, é possível aprender sobre:

* Programação de microcontroladores com ESP32.
* Utilização de sensores ultrassônicos.
* Controle de servo motores.
* Estruturas condicionais `if` e `else`.
* Leitura de dados pelo Monitor Serial.
* Automação de sistemas de estacionamento.

## 👩‍💻 Autoria

Projeto desenvolvido para fins educacionais, com o objetivo de praticar programação em C++, eletrônica e automação utilizando o ESP32.
