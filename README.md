# Progetto_PO_DEC
 <h1 align="center"> Progetto programmazione ad oggetti fidwork </h1>

<p align="center">
Questo progetto ha lo scopo di creare un sistema che permetta ad un utente di poter cercare un lavoro potendo filtrare la ricerca con diversi parametri
</p>

* [Introduzione](#intro)
* [Diagrammi uml](#uml)
* [rotte](#rotte)
* [/Sug](#/Sug)
* [/Filter](#/Filter)
* [/Static](#/Static)
* [Eccezzioni](#Eccezzioni)
<a name="intro"></a>
## Introduzione
Il nostro progetto permette all'utente di ricercare lavori attraverso il filtraggio di alcuni parametri come (ruolo,data,location,tipo,linguaggio ecc...),l'utente inoltre potrà visualizzare delle statistiche come (percentuale lavoro remoto e non ,quanti ruoli sono disponibili per quel linguaggio ecc...) riguardanti ad esempio il linguaggio scelto, il sistema infine ha la possibilità di suggerire all'utente 5 città.  

## Possibilità aggiuntive del sistema
🟡: possibilità di filtraggio delle statistiche e dei lavori per tutte le variabili(data,location,ruolo,tipo...)

🟡: statistiche dei lavori anche con percentuali 

🟡: Classe di test


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

<a name=Eccezzioni></a>
## Eccezzioni 

   * Nel caso in cui l'utente dimentichi di inserire il nome della città viene generata un'eccezione del tipo ***EmptyStringException*** che restituisce un messaggio di questo tipo:
   
```
Hai dimenticato di inserire la città...
     
```

  * Nel caso in cui l'utente inserisca una città non ammessa viene generata un'eccezione del tipo ***CityNotFoundException*** che restituisce un messaggio di questo tipo:

   ```
    Tolentì non è presente nello storico. Puoi scegliere tra: "Ancona", "Campobasso", "Macerata", "Roma", "San Martino in Pensilis" e "Tolentino".
   ```

   * Invece se viene inserito un periodo diverso da quelli sopra citati viene generata un'eccezione del tipo ***WrongPeriodException*** che restituisce un messaggio di questo tipo:

   ```
    mensile non è permessa. Devi inserire una stringa tra "giornaliera","settimanale" e "trisettimanale".
   ```


<a name="test"></a>
## Test

Abbiamo implementato i seguenti [test](https://github.com/FedericaParlapiano/Progetto-Programmazione-Ad-Oggetti/tree/master/WeatherApp/src/test/java/com/project/WeatherApp) per verificare il corretto funzionamento di alcuni metodi e alcune eccezioni

![alt_text](https://github.com/FedericaParlapiano/Progetto-Programmazione-Ad-Oggetti/blob/master/UML/Test.jpg)



<a name="doc"></a>
## Documentazione
Il codice java è interamente documentato in [Javadoc](https://github.com/StomaticSP8/Progetto_PO_DEC/tree/prova_1/PPO_Dicembre/doc).


<a name="autor"></a>
### Autori
Progetto realizzato da:
- Antonio Zaccardi (50%)
- Francesco Cerrone (50%)

