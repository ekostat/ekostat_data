# ekostat_data
## Data
Data är hämtade från datavärdskapet för Marina miljöövervakningsdata på [SMHI](www.smhi.se), [sharkweb](https://www.smhi.se/klimatdata/oceanografi/havsmiljodata/marina-miljoovervakningsdata). Senaste uttaget gjordes 2019-03-05.

Uttaget från sharkweb har körts genom de första stegen i [ekostat_calculator](https://github.com/ekostat/ekostat_calculator) för att ta fram grunddata för beräkning av ekologiskstatus enligt bedömningsgrunderna för kustvatten i HVMFS 2013:19. 

Filen WATERS_export.txt innehåller en punkt per mättillfälle för varje parameter och endast ifrån de månader som specificeras i HVMFS 2013:19 för respektive parameter. Mättillfille identifieras genom kolumnan SAMPLE_ID. 

### Klorofyll
För varje datum plockas utifrån typområde och stationsdjup antingen ytvärde (0 m) eller integreratvärde 0-10 m: 

**Ytvärde**
*	som ytvärde räknas i första hand flaskdata < 2m från flaskdata
*	i andra hand tas data från slangprov med maxdjup < 2m
*	i tredje hand tas data data från den datatyp som har rapporterat data på minsta djup. Detta ger kommentaren *Expert judgement not surface sample*.

**Integrerat värde**:
*	i första hand tas data från slangprovtagning mellan (0-1 m) – (9-11 m)
*	i andra hand tas data från beräknat integrerat värde från flaskdata mellan (0-1 m) – (9-11 m)
*	i tredje hand tas data från slangprovtagning med maxdjup <11 m. Detta ger kommentaren *Expert judgement. Integrated data to shallow.*
* i fjärde hand tas flaskdata från det grundaste djup (< 10 m) som det rapporterats på. Detta ger kommentaren *Expert judgement to shallow data from discrete sample.*

### Syre
I vattenförekomsten Askirkefjärden har fem tillfällen med djup 112 m ändrats till 11.2 m. Detta ska uppdateras i sharkweb till rätt djup.
Endast syre data från djupaste mätningen i varje profil tas med och endast data från djup som ligger max 10 ovanför max djup i vattenförekomsten. Maxdjupet hämtas från hypsografen för vattenförekomsten. Då hypsograferna inte alltid får med det faktiska maxdjupået så förekommer ibland mtädjup större än hypsografens maxdjup, dessa data kommer naturligtvis också med. 
Vattenförekomst Vivassen har ett rapporterat mätdjup på 82.5 m 2017-06-12, detta är inte korrekt och kommer att rättas upp, men är i denna version ej rättad.
Procent påverkat area beräknas och visas för att vattenförekomster och stationer, men ska endast användas för klassning i de vattenförekomster som specificeras i föreskriften (HVMFS 2013:19). Vilka vattenförekomster detta gäller och vilka stationer som använts visas nedan i tabell.

Typomr | MS_CD	| Vattenförekomst | Station | Vattenförekomst i HVMFS 2013:19
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
Siktdjup är hämtat för varje provtagningstillfälle

### BQI
BQI är hämtat från varje provtagningstillfälle

## WATERS Statusklassning
De data som finns här har sedan använts för att beräkna status och osäkerhet och presenteras i WATERS gränssnitt för detta, [http://3.120.131.94/ekostat/]

