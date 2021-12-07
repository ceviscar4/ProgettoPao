# Progetto_PO_DEC
 <h1 align="center"> Progetto programmazione ad oggetti findwork </h1>

<p align="center">
Questo progetto ha lo scopo di creare un sistema che permetta ad un utente di poter cercare un lavoro potendo filtrare la ricerca con diversi parametri
</p>

* [Introduzione](#intro)
* [Diagrammi uml](#uml)
* [rotte](#rotte)
* [/Sug](#/Sug)
* [/Filter](#/Filter)
* [/Static](#/Static)
* [Eccezzioni](#Eccezioni)
* [Possibilità aggiuntive del sistema](#plus)
* [Test](#Test)
* [Documentazione javadoc](#documentazione)
<a name="intro"></a>
## Introduzione
Il nostro progetto permette all'utente di ricercare lavori attraverso il filtraggio di alcuni parametri come (ruolo,data,location,tipo,linguaggio ecc...),l'utente inoltre potrà visualizzare delle statistiche come (percentuale lavoro remoto e non ,quanti ruoli sono disponibili per quel linguaggio ecc...) riguardanti ad esempio il linguaggio scelto, il sistema infine ha la possibilità di suggerire all'utente 5 città.  

<a name="uml"></a>
## Diagrammi UML

*Use Case Diagram*

![alt text](https://github.com/StomaticSP8/Progetto_PO_DEC/blob/prova_1/Screenshot%20(6).png)

***

*Class Diagram*

![alt text](https://github.com/StomaticSP8/Progetto_PO_DEC/blob/prova_1/Screenshot%20(7).png)

***


*Sequance Diagram (parte 1)*

![alt_text](https://github.com/StomaticSP8/Progetto_PO_DEC/blob/prova_1/work-project%20Sequence%20Diagram.jpg)

***


<a name="rotte"></a>
## Rotte
Le chiamate verranno gestite dalla porta:
```
localhost:8080
```
Queste sono le chiamate possibili:

N° | Tipo | Rotta | Descrizione
----- | ------------ | -------------------- | ----------------------
[1](#1) | ` GET ` | `/Sug` | *Restituisce un vettore di città con 5 città consigliate da parte del sistema .*
[2](#2) | ` POST ` | `/Filter` | *Questa rotta applica i filtri che abbiamo creato e restituisce un json con tutti i lavori filtrati in base ai dati inseriti nel body di postman.*
[3](#3) | ` POST ` | `/Static` | *Questa rotta effettua le statistiche che possono essere filtrate, restituisce un oggetto chiamato parametri_statistica in formato json contenete percentuale lavori in remoto e non, altri linguaggi di programmazione oltre java .*


* ## Come può l'utente effettuare richieste? Cosa riceverà in risposta? 

Basta avviare il programma come applicazione SpringBoot, assicurarsi di avere Postman (o simili) e seguire le istruzioni che stiamo per darvi.

Innanzitutto non bisogna confondere le richieste di tipo GET con quelle di tipo POST, altrimenti riceverà un messaggio di errore.
Ora illustreremo alcuni esempi su cosa dare in richiesta e cosa dovete aspettarvi in risposta.

<a name="/Sug"></a>
## 1.   /Sug

La prima rotta è di tipo GET /Sug suggerisce all'utente 5 città americane che vengono restituite come un vettore di citta 

![alt_text](https://github.com/ceviscar4/ProgettoPao/blob/main/Screenshot%20(9).png)

<a name=/Filter></a>
## 2.   /Filter

La seconda rotta è di tipo POST /Filter permette il filtraggio dei seguenti parametri (location,location2,location3,role,data,employement_type,remote,keywords), all'interno del body su postman l'utente dovrà inserire anche il numero_citta tale numero va da 1 a 3, quindi l'utente può filtrare più location e filtrarli per tutti i parametri elencati in precedenza.
ESEMPIO BODY
```
{
"location":"london",        [esempio prima città da filtrare]
"location2":"india",         [esempio seconda città da filtrare]
"location3":"california",    [esempio terza città da filtrare]
"numero_citta":"3",          [numero di città da filtrare, se il numero di città non è uguale a quello delle locazioni inserite verrà lanciata un eccezione] 
"remote":"false",            [filtra per tutte le locazioni inserite il parametro remote:false]
"keywords":"python"          [filtra per tutte le locazioni il linguaggio python] 
}
```
Il risultato sarà un vettore di JSONObject contenente tutti i risultati filtrati per (remote,keywords) per la prima locazione(location), per la seconda locazione(location2) e per la terza locazione(location3)..
![alt_text](https://github.com/ceviscar4/ProgettoPao/blob/main/Screenshot%20(11).png)



<a name=/Static></a>
## 3.    /Static

La terza rotta è di tipo POST e il body viene scritto allo stesso modo del /Filter, vediamo un esempio:

![alt_text](https://github.com/ceviscar4/ProgettoPao/blob/main/Screenshot%20(16).png)

<a name=Eccezioni></a>
## Eccezioni 

   * In caso di mancato inserimento del numero_citta nel body per la seconda e terza rotta verrà lanciata un eccezione ***Exception_numero_citta*** e restituisce un messaggio:
   
```
Inserire il numero di citta da trovare all'interno dell body con la seguente sintassi: numero_citta=
     
```

  * In caso di mancato inserimento di testo nel body nella seconda e terza rotta verrà lanciata un eccezione ***input_exception*** e restituisce un messaggio:

   ```
    il body e vuoto.
   ```
<a name="plus"></a>
## Possibilità aggiuntive del sistema
🟡Il programma svolge tutte le funzioni che ci sono state assegnate, solamente la top 5 lavori non siamo riusciti a svolgere per rimediare a tale mancanza abbiamo aggiunto più filtri alle statistiche (remote,role,keywords), le statistiche vengono fatte su un massimo di 3 città, inoltre vengono visualizzate anche le percentuali di lavoro in remoto e non.

🟡Per i risultati filtrati abbiamo aggiunto la possibilità di filtraggio con(data,keywords).

🟡Il nostro programma non si limita solamente a trovare i lavori in linguaggio java ma l'utente potrà cercare qualsiasi tipo di lavoro con i filtri che desidera 

<a name="Test"></a>
## Test

Abbiamo implementato anche una classe di test che testa l'eccezione ***input_exception***


[Test](https://github.com/StomaticSP8/Progetto_PO_DEC/blob/prova_1/PPO_Dicembre/src/test/java/com/example/PPO_Dicembre/testclass.java)



<a name="documentazione"></a>
## Documentazione
La documentazione javadoc è presente in questo link [Javadoc](https://github.com/StomaticSP8/Progetto_PO_DEC/tree/prova_1/PPO_Dicembre/doc).


<a name="autor"></a>
### Autori
Progetto realizzato da:
- Antonio Zaccardi (50%)
- Francesco Cerrone (50%)

