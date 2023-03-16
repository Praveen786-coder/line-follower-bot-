# line-follower-bot-
int D2 = 2; //motor a = +
int D3 = 3; //motor a = -
int D4 = 4; //motor b = -
int D5 = 5; //motor b = +

void setup() {
pinMode(D4, OUTPUT);
pinMode(D5, OUTPUT);
pinMode(D2, OUTPUT);
pinMode(D3, OUTPUT);
  
Serial.begin(9600);
pinMode(6, INPUT);  //IR_Left
pinMode(7, INPUT);   //IR_center
pinMode(8, INPUT);   //IR_Right
}

void loop() {
 int X = digitalRead(6);
 Serial.print("Left=");
 Serial.println(X);
 int Y = digitalRead(7);
 Serial.print("Center=");
 Serial.println(Y);
 int Z = digitalRead(8);
 Serial.print("Right=");
 Serial.println(Z);
 if ((digitalRead(X) == 0)&&(digitalRead(Y) == 1)&&(digitalRead(Z) == 0)){forword();}
 if ((digitalRead(X) == 0)&&(digitalRead(Y) == 0)&&(digitalRead(Z) == 1)){turnLeft();}
 if ((digitalRead(X) == 1)&&(digitalRead(Y) == 0)&&(digitalRead(Z) == 0)){turnRight();}
 if ((digitalRead(X) == 1)&&(digitalRead(Y) == 1)&&(digitalRead(Z) == 1)){Stop();}
}
void forword(){
digitalWrite(D2, HIGH);
digitalWrite(D3, LOW);
digitalWrite(D4, HIGH);
digitalWrite(D5, LOW);  
}


void turnRight(){
digitalWrite(D2, HIGH);
digitalWrite(D3, LOW);
digitalWrite(D4,LOW);
digitalWrite(D5, LOW);  
}

void turnLeft(){
digitalWrite(D2, LOW);
digitalWrite(D3, LOW);
digitalWrite(D4, HIGH);
digitalWrite(D5, LOW);
}

void Stop(){
digitalWrite(D2, LOW);
digitalWrite(D3, LOW);
digitalWrite(D4, LOW);
digitalWrite(D5, LOW);
}
