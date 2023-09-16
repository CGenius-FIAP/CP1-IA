# CP-IA 🤖✨

Repositório referente aos projetos que serão desenvolvidos durante os 3 Checkpoints de IA/IoT.

## Recursos 📚

- **Link do vídeo explicativo**: [Vídeo explicativo no Youtube](https://youtu.be/TeAZm4yEqEg)🎥
- **Link do projeto no Tinkercad**: [Veja o projeto no Tinkercad](https://www.tinkercad.com/things/1VzUMFYxqJB) 🛠

## Código Fonte 📜

```
#include <LiquidCrystal.h>

const int soilSensorPin = A0;
const int lightSensorPin = A1;

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  pinMode(soilSensorPin, INPUT);
  pinMode(lightSensorPin, INPUT);
  
  Serial.begin(9600);
  lcd.begin(16, 2);  
  lcd.print("Solo:");  
}

void loop() {
  int soil = analogRead(soilSensorPin);
  int light = 1023 - analogRead(lightSensorPin);
  
  Serial.print("Solo: "); Serial.println(soil);
  Serial.print("Luz: "); Serial.println(light);

  lcd.setCursor(6, 0);
  int sp = map(soil, 0, 1023, 0, 100);

  if (sp > 80) lcd.print("Encharcado");
  else if (sp >= 60) lcd.print("Umido     ");
  else if (sp >= 40) lcd.print("Lev. Seco ");
  else if (sp >= 25) lcd.print("Regar logo");
  else lcd.print("Regar     ");

  lcd.setCursor(0, 1);
  lcd.print("Luz: ");
  lcd.print(light);

  if (light > 1007) lcd.print("(EXCEL)");
  else lcd.print("         ");

  delay(1000);
}
```

## Integrantes 👥
- Filipe Santos 
- Jorge Camara 
- Vitor Madureira

15/09/23
