int led = 9;
int sensor = 8;
int buzzer = 10;
int state = LOW;
int val = 0;

void setup()
{
  pinMode(led,OUTPUT);
  pinMode(sensor, INPUT);
  pinMode(buzzer,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  val = digitalRead(sensor);
  if (val == HIGH)
  {
    // check if the sensor is HIGH
    digitalWrite(led,HIGH);
    delay(100);
    if (state == LOW)
    {
      Serial.println("Motion detected!");
      tone(buzzer,1000);
      state = HIGH;
    }
  }
  else
  {
    digitalWrite(led,LOW);
    delay(200);
    if (state == HIGH)
    {
      Serial.println("Motion stopped!");
      noTone(buzzer);
      state = LOW;}}}
 
