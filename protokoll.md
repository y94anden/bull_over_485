# Protokollet

* Bussen styrs av en master
* Enheterna ska ha en unik adress på nätet


# xBull (extended bull)

Möjligt format:

Address, command, parameter, length, payload, checksum

Adressen skulle kunna vara en byte där bara de lägsta 7 bittarna används.
Om MSB sätts betyder det att det kommer ytterligare en adress byte
direkt efter. Detta skulle kunna ge oändligt antal möjliga adresser om så
önskas.


# Fråga efter okända/okonfigurerade enheter

Ett möjligt sätt att enumerera enheter utan att känna till dem kan vara
att mastern sätter upp ett antal tidsluckor och ber att enheterna väljer
en lucka slumpmässigt. I denna lucka skickar de sin adress och vilken
tidslucka de önskar i nästa frame.

Första gången chansar enheterna på att en tidslucka är ledig och allokerar
en lucka för nästa omgång. Om två eller fler enheter krockar, så har de
förhoppningsvis valt olika tidsluckor för nästa omgång.

När det är dags för en enhet att sända i sin tidslucka, så väljer den en
tidslucka för nästa omgång som den inte har hört någon annan välja.

Mastern skulle sedan kunna välja att adressera en enhet med kombinationenen
av dess adress och dess senaste valda tidslucka för att differentiera mellan
två enheter om de har samma adress eller är okonfigurerade (har adressen 0).


# Uppgradering

Mastern ber en adresserad enhet att gå i uppgraderingsläge och resten av
enheterna att gå i viloläge.

All efterkommande trafik är enbart avsedd för enheten som ska uppgraderas.
Övriga enheter vilar tills bussen har varit tyst i X sekunder.

Eller man trycker på uppdateringen på en device men kan prata med andra emellan om man vill. 

Eventuellt olika uppdateringsförfaranden för olika typer av devices. 

Tex för en fpga (altera) utan processor så kan man helt enkelt ange att det är en skrivning till confminnet och vilken adress det ska börja på. När man sen skrivit all data kan man tala om att den har en uppdatering som ska köras från den aktuella adressen. 
