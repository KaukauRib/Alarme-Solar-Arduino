# 🔆 Alarme de Baixa Geração Solar com Arduino

Este projeto utiliza um painel solar e um Arduino Uno para monitorar a geração de energia solar. Quando a geração cai abaixo de um nível mínimo, um alarme sonoro é ativado.

---

## Link do Projeto no Tikercad
[Alarme Solar](https://www.tinkercad.com/things/e82HkvN8WWK-alarme-solar)

---

## ⚙ Funcionalidades

- Leitura da tensão gerada por um painel solar
- Acionamento automático de alarme (buzzer) em baixa geração
- Código simples com Arduino
- Possibilidade de expansão com Wi-Fi, LCD, ou data logging

---

## 🧰 Tecnologias Utilizadas

- *Arduino Uno*
- *Tinkercad (simulação)*
- *C/C++ (Arduino IDE)*

---

## 🗂 Arquitetura do Projeto

### 1. Componentes Necessários
- Arduino Uno
- Painel solar (5V)
- Buzzer ativo
- Resistor 220Ω
- Protoboard
- Fios jumper

### 2. Montagem
Conecte o painel solar ao pino A0 (positivo) e GND. Conecte o buzzer ao pino digital 8 com resistor em série.

### 3. Código
// Definições dos pinos
const int pinoSolar = A0;     // Entrada analógica conectada ao painel solar
const int pinoAlarme = 8;     // Saída digital conectada ao buzzer

// Limiar de tensão para o alarme (ajustável conforme necessidade)
const int limiarSolar = 900;  // Valor de referência da tensão baixa

void setup() {
  pinMode(pinoAlarme, OUTPUT);
  Serial.begin(9600);  // Para monitoramento da tensão no Serial Monitor
}

void loop() {
  int leituraSolar = analogRead(pinoSolar);  // Lê a tensão do painel solar

  Serial.print("Tensão Solar (valor analógico): ");
  Serial.println(leituraSolar);

  // Se a tensão estiver abaixo do limiar, liga o alarme
  if (leituraSolar < limiarSolar) {
    digitalWrite(pinoAlarme, HIGH);  // Liga o buzzer
  } else {
    digitalWrite(pinoAlarme, LOW);   // Desliga o buzzer
  }

  delay(500); 
}

---

## 🧪 Resultados Esperados

| Condição                   | Leitura (A0) | Resultado         |
|----------------------------|--------------|-------------------|
| Alta produção de energia   | > 900        | Alarme desligado  |
| Baixa produção de energia  | < 900        | Alarme ligado     |

