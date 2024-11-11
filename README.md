Izveštaj o Statičkoj Analizi Koda
Zapažanja po Fajlovima
Fajl: Calculator.java – 134 linija
Linija 7: static float finalResult; — globalna promenljiva može izazvati probleme ako više niti koristi istu instancu kalkulatora, što znači da kôd nije niti-bezbedan.
Linija 12-19: Operations klasa — mogla bi biti pojednostavljena. Metoda ToString() kombinuje simbole u string, ali se koristi samo za prepoznavanje simbola, što može biti optimizovano.
 Linija 24: Run metoda — mogla bi imati bolji naziv, kao što je evaluate ili calculate, kako bi bilo jasnije šta metoda radi.
Linija 30: evaluateExpression — metoda sadrži mnogo logike. Mogla bi se refaktorisati u manje metode radi veće čitljivosti.
Linija 37: expression.charAt(0) — potrebno je proveriti da li expression ima barem jedan karakter pre nego što pristupite prvom elementu, kako biste izbegli potencijalne izuzetke.
Linija 46: String[] numbers = expression.split(...) — ovo rešenje radi, ali metoda split može izazvati probleme ako naiđe na neispravne izraze ili prazne stringove.
Linija 53-61: Kreiranje operationList — možete optimizovati tako što biste ovu logiku premestili u posebnu metodu za parsiranje operacija.
Linija 65-75: Parsiranje brojeva — Float.parseFloat može izazvati NumberFormatException. Možete dodati detaljnije obaveštenje za korisnika o grešci.
Linija 81: Calculate metoda — rekursivni poziv može izazvati greške sa prevelikim izraza ili dovesti do prekoraka steka (StackOverflowError). Možda biste mogli koristiti iterativni pristup za izračunavanje.
Linija 91-148: Blok Calculate — logika za izračunavanje je prekomplikovana. Refaktorisanje u manje funkcije za različite operacije (npr. calculateMultiplication, calculateDivision) povećalo bi čitljivost.
Fajl: Start.java -  19 linija
Linija 6-Zapažanje: Varijabla String Expression ne koristi standardnu Java konvenciju imenovanja (camelCase).
Linija 8-Zapažanje: Promenljiva boolean active = true; koristi se za kontrolu glavne petlje. Postoji alternativa u strukturi do-while, ali nije neophodna.
Linija 11-Zapažanje: Scanner scanIn; je definisan unutar petlje. Ovo može dovesti do neefikasnog upravljanja resursima i potencijalnog resursnog curenja.
Linija 13-Zapažanje: scanIn = new Scanner(System.in); u svakoj iteraciji petlje kreira novi objekat Scanner, što može dovesti do prekomernog korišćenja resursa.
Linija 16-Zapažanje: if (Expression.equals("exit")) { — poređenje stringova je ispravno, ali nije neosetljivo na velika i mala slova.
Linija 17 -Zapažanje: scanIn.close(); unutar if bloka može zatvoriti Scanner pre vremena, što može izazvati probleme ako System.in treba ponovo koristiti.
Linija 19 -Zapažanje: Calculator.Run(Expression) metoda može izazvati nepredviđene greške ako unos nije ispravan.
