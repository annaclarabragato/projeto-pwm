# projeto-pwm

1. [Introdução ao PWM](#introdução-ao-pwm)
2. [Componentes necessários](#componentes-necessários)
3. [Esquemático](#esquemático)
4. [Código-fonte](#código-fonte)
5. [Instruções de montagem](#instruções-de-montagem)
6. [Funcionamento do projeto](#funcionamento-do-projeto)

![image](https://github.com/annaclarabragato/projeto-pwm/assets/125417531/239955c4-cbc7-4a8c-9b47-35002ba4869c)

#include <Arduino.h>


const int motor = 9; 
const int button = 2;

int motorstate = LOW;
int buttonState = LOW;
int lastButtonState = LOW;

void setup() {
  pinMode(button, INPUT_PULLUP);
}

void loop() {

buttonState = digitalRead(button);
if(buttonState == HIGH && lastButtonState == LOW){
    motorstate++;
    if (motorstate == 0){
        analogWrite(9, 255);

    }else if (motorstate == 1){
        analogWrite(9, 191);

    }else if (motorstate == 2){
        analogWrite(9, 127);

    }else if (motorstate == 3){
        analogWrite(9, 64);

    }else if (motorstate == 4){
        analogWrite(9, 0);

    }else if (motorstate == 5){
        analogWrite(9, 255);
        motorstate = 0;
    }
}
lastButtonState = buttonState;
}
