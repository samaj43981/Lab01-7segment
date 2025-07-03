const int segmentPins[] = {19, 18, 17, 16, 15, 14, 13};

const byte digitPatterns[][7] = {
  {1, 1, 1, 1, 1, 1, 0},
  {0, 1, 1, 0, 0, 0, 0},
  {1, 1, 0, 1, 1, 0, 1},
  {1, 1, 1, 1, 0, 0, 1},
  {0, 1, 1, 0, 0, 1, 1},
  {1, 0, 1, 1, 0, 1, 1},
  {1, 0, 1, 1, 1, 1, 1},
  {1, 1, 1, 0, 0, 0, 0},
  {1, 1, 1, 1, 1, 1, 1},
  {1, 1, 1, 1, 0, 1, 1}
};

void setup() {
  Serial.begin(115200);
  Serial.println("trigger");

  for (int i = 0; i < 7; i++) {
    pinMode(segmentPins[i], OUTPUT);
  }
}

void displayDigit(int digit) {
  if (digit < 0 || digit > 9) {
    for (int i = 0; i < 7; i++) {
      digitalWrite(segmentPins[i], LOW);
    }
    return;
  }

  for (int i = 0; i < 7; i++) {
    digitalWrite(segmentPins[i], digitPatterns[digit][i]);
  }
}

void loop() {
  for (int digit = 0; digit <= 9; digit++) {
    displayDigit(digit);
    delay(1000);
  }
}
![esp32](https://github.com/samaj43981/Lab01-7segment/blob/main/66030067/image.png)
