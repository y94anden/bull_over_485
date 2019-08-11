# Hårdvara

Man skulle möjligen kunna använda en Arduino Mini elle Nano. Fördelen med Nano
är att man kan koppla den direkt med USB till en dator för programmering
och testning utan att behöva ett RS485-nät.

Man kan också tänka sig att göra hela hårdvaran själv, och bestycka den med en
ATMega328p och en kristall. Det blir antagligen inte billigare än att köpa en
hel Arduino Nano.


# Arduino Nano

Den har bara en UART som är kopplad till USB'n. Detta behöver inte vara ett
problem. Måste testas.

Man kan också köra en software serial på vilka pinnar som helst. Även den
befintliga [optiboot] kan köras mot en software serial, troligen även med
angivande av RS485-enable pinne. Det borde då gå att köra [avrdude] för
uppgradering, eller kanske direkt från Arduino-IDE't.

Arduinon kan matas med upp till 12V utan problem, men kan också direktmatas
med 5V.

Mycket kod finns redan till Arduino för diverse saker, t.ex. onewire.

Det går att göra allt med en Arduino som dess processor (ATMega328p) klarar,
eventuellt får man kasta ut Arduinos framework och skriva koden själv i C/C++
och kompiera med [avr-gcc].

Den egenutvecklade hårdvaran skulle då göras i form av ett shield till denna.

## Shield

Detta shield behöver ha:

* Powersupply
* rs485-drivare
* möjligt att bestycka med 1-wire drivare
* möjligt att bestycka med drivare för I/O och pwm.
* spänningsdelare från power supply till en A/D pinne för spänningsmätning.



[optiboot]: https://github.com/Optiboot/optiboot
[avrdude]: https://www.nongnu.org/avrdude/
[avr-gcc]: https://gcc.gnu.org/wiki/avr-gcc
