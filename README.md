# ekostat_data
## Data
Data är hämtade från datavärdskapet för Marina miljöövervakningsdata på [SMHI](www.smhi.se), [sharkweb](https://www.smhi.se/klimatdata/oceanografi/havsmiljodata/marina-miljoovervakningsdata). <br>Senaste uttaget gjordes 2019-05-08. De data som finns här används sedan för att beräkna status och osäkerhet vilket presenteras i WATERS gränssnitt för detta, http://3.120.131.94/ekostat/. De nya data finns troligen i WATERS-verktyget den 14 maj eller tidigare.

Uttaget från sharkweb har körts genom de första stegen i [ekostat_calculator](https://github.com/ekostat/ekostat_calculator) för att ta fram grunddata för beräkning av ekologiskstatus enligt bedömningsgrunderna för kustvatten i HVMFS 2013:19. 

Filen WATERS_export.txt innehåller en punkt per mättillfälle för varje parameter och endast ifrån de månader som specificeras i HVMFS 2013:19 för respektive parameter. Mättillfälle identifieras genom kolumnan SAMPLE_ID. Det enklaste sättet att ladda ner .txt-filen är att ladda ner hela den folder som ett .zip-paket, [direktlänk](https://github.com/ekostat/ekostat_data/archive/master.zip)

I vissa vattenförekomster vill man ta med stationer i intilliggande vattenförekomster i statusberäkningen. Detta är löst genom att data har duplicerats men fått vattenförekomst-ID (MS_CD) för den vattenförekomst som stationen ska inkluderas i. Därav finns en kolumn som heter WB_ID_original. Om det är något mer län där man behöver lägga till stationer från intilliggande vattenförekomster, kontakta Lena Viktorsson på SMHI.

#### Nytt
***Noll-värden för BQI är med i uttaget genom att parametern "No species" har tagits med. Se mer detaljer nedan under rubriken BQI.***

***Extra uttag av stationen Tavlefjärden N, som ska användas för klassning av Tavlefjärden men som med nuvarande position i shark ligger i Umeå älvens utlopp.***

***Stationsfilter för stationen HÖ3, exkluderas från Megrundsområdet (WA86698934) och inkluderas i Hörnefors (WA27609565).***

***Undantag för syre från Koljöfjorden, data kommer med från >= 39 m trots att maxdjup på stationen är 70 m.***

### Klorofyll
För varje datum plockas utifrån typområde och stationsdjup antingen ytvärde (0 m) eller integreratvärde 0-10 m: 

**Ytvärde**
*	som ytvärde räknas i första hand flaskdata <2m från flaskdata
*	i andra hand tas data från slangprov med maxdjup <2m
*	i tredje hand tas data data från den datatyp som har rapporterat data på minsta djup (<10 m). Detta ger kommentaren *Expert judgement. This is not true surface sample*.

**Integrerat värde**:
*	i första hand tas data från slangprovtagning mellan (0-1 m) – (9-11 m)
*	i andra hand tas data från beräknat integrerat värde från flaskdata mellan (0-1 m) – (9-11 m)
*	i tredje hand tas data från slangprovtagning med maxdjup <9 m. Detta ger kommentaren *Expert judgement. Integrated data to shallow.*
* i fjärde hand tas flaskdata från det grundaste djup (<10 m) som det rapporterats på. Detta ger kommentaren *Expert judgement. Not integrated sample.*

### Syre
Endast syre data från djupaste mätningen i varje profil tas med och endast data från djup som ligger max 10 ovanför max djup i vattenförekomsten. Maxdjupet hämtas från hypsografen för vattenförekomsten. Då hypsograferna inte alltid får med det faktiska maxdjupået så förekommer ibland mtädjup större än hypsografens maxdjup, dessa data kommer naturligtvis också med. *Undantag för syre från Koljöfjorden, data kommer med från >= 39 m trots att maxdjup på stationen är 70 m.*

Procent påverkad area beräknas och visas för alla stationer, men ska endast användas för klassning i de vattenförekomster som specificeras i föreskriften (HVMFS 2013:19). Vilka vattenförekomster detta gäller och vilka stationer som använts visas nedan i tabell.

Typomr | MS_CD	| Vattenförekomst | Station | Vattenförekomst (station) i HVMFS 2013:19
------ | ------ | --------------- | ------- | --------------------------------
2	|WA43270311	|Havstensfjorden	|HAVSTENSFJORD	|Havstensfjord (Havstensfjord)
2	|WA23971566	|Koljö fjord	|KOLJÖFJORD	|Koljöfjord (Koljöfjord)
2	|WA46670058	|Gullmarn centralbassäng	|ALSBÄCK	|Gullmarn centralbassäng (Alsbäck)
2	|WA29111809	|Byfjorden	|BYFJORDEN	|Byfjorden (Byfjorden)
5	|WA55983181	|Laholmsbuktens kustvatten	|YTTRE LAHOLMSBUKTEN	|Laholmsbuktens kustvatten (Hallands väderö)
5	|WA12817029	|N Öresunds kustvatten	|ÖVF 1:1 HÖGANÄS	|N Öresunds kustvatten (Kullen)
5	|WA99366628	|Skäldervikens kustvatten	|SKÄLDERVIKEN	|Skälderviken (S2)
5	|WA52813004	|Skälderviken	|S-5	|Skälderviken (S5)
6	|WA61585185 	|N m Öresunds kustvatten	| W LANDSKRONA	|N m Öresunds kustvatten (W-Landskrona)
12n	|WA68382937	|Kanholmsfjärden	|S86 KANHOLMSFJÄRDEN	|Kanholmsfjärden (Kanholmsfjärden)
24	|WA46408217	|Lilla Värtan	|KARANTÄNBOJEN	|Tranholmenområdet (Ekhagen)
24	|WA36243146	|Skurusundet	|LÄNNERSTASUNDET	|Skurusundet (Lännerstadssundet)
24	|WA17695227	|Askrikefjärden	|ASKRIKEFJÄRDEN	|Askrikefjärden (Älvvik)

### Näringsämnen
Näringsämne och salt är medelvärdesbildat 0-10 m vid varje provtagningstillfälle.

### Siktdjup
Siktdjup är hämtat för varje provtagningstillfälle.

### BQI
BQI är hämtat från varje provtagningstillfälle.
Zoobenthos data innehåller både parametern BQIm och ”No species” från sharkweb. För No species har endast mätningar med ingen kommentar eller en kommentar som enkelt kan sorteras ut som att den indikerar att inga djur hittats använts. Se separat fil för vilka data frö ”No species” som inte tagits med (55 tillfällen).
Alla BQI-värden är beräknade av datavärd (SMHI) och har nyligen kontrollerats av utomstående expertar. Alla värdena följer föreskriften HVMFS 2013_19.
