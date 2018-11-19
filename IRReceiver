#include <IRremote.h>

int recvPin = 10;
IRrecv irrecv(recvPin);

void  setup ( )
{
  Serial.begin(9600);   // Status message will be sent to PC at 9600 baud
  pinMode(13, OUTPUT);
  irrecv.enableIRIn();  // Start the receiver
}

void  loop ( )
{
  decode_results  results;        // Somewhere to store the results
  int key;

  if (irrecv.decode(&results)) {  // Grab an IR code
    if (results.value != 0xFFFFFFFF) {
      Serial.print("Code      : ");
      Serial.println(results.value, HEX);     

      switch (results.value) {
        case 0xFF30CF:
          key = 1; digitalWrite(13, HIGH); break;
        case 0xFF18E7:
          key = 2; digitalWrite(13, LOW); break;
        case 0xFF7A85:
          key = 3; break;
        case 0xFF10EF:
          key = 4; break;
        case 0xFF38C7:
          key = 5; break;
        case 0xFF5AA5:
          key = 6; break;
        case 0xFF42BD:
          key = 7; break;
        case 0xFF4AB5:
          key = 8; break;
        case 0xFF52AD:
          key = 9; break;
        case 0xFF6897:
          key = 0; break;
        case 0xFFE01F:
          key = 'm'; break;
        case 0xFFA857:
          key = 'p'; break;
        default:
          key = 'u'; break;
      }

      Serial.print("Key: "); Serial.println(key);
    }
    irrecv.resume();              // Prepare for the next value
  }
}
