# Period-2-Node.js-Express-JavaScript-Backend-Testing-NoSQL-MongoDB-and-Mongoose
---
## 1. Why would you consider a Scripting Language as JavaScript as your Backend Platform?
---

• Det er nemt og hurtigt, at opbygge og opsætte et arbejdsnetværksprogram (a working network application) med node.js og den rigtige editor.

• Det er meget praktisk, at du kan bruge det samme sprog både i front-end og i back-end.

• Der kræves ikke meget kode for, at en applikation kan køre.


---
## 2. Explain Pros & Cons in using Node.js + Express to implement your Backend compared to a strategy using, for example, Java/JAX-RS/Tomcat

---

### PROS
•	Man kan lave en hurtig response network application, hvis det er gjort rigtigt. 

•	Tillader at sende filer hurtigt igennem datastreaming og hurtige filoverførsler (file uploads). 

•	Det er nemt at opsætte en REST-API med Express application generator som et brugerdefineret standardprojekt, Express. 


Først install node.js https://nodejs.org/en/
bagefter install.
https://expressjs.com/en/starter/installing.html her guide 
```
npm install express -g
```
Hvad navn skal hedder på expres projektet.
```
express Navnpåprojektet
cd Navnpåprojektet
npm install
npm start 
```
Så er man hurtigt i gang med express projekt. 

•	Det er effektivt at håndtere tusindvis af samtidige anmodninger (for eksempel-en chat applikation). 

•	Det er meget simpelt at implementere server middleware, der vil blive udført imellem alle request (hvis requerment er tilladt).

### CONS

•	Java er god til at håndtere CPU-tunge opgaver, Node.JS + Express er ikke. Fordi Node er, på trods af sin asynkronhændelsesmodel, af 
natur enkelttrådet. Når du starter en Node-proces, kører du en enkelt proces med en enkelt tråd på en enkelt kerne. Så din kode vil ikke blive udført parallelt, kun I/O-operationer er parallelle, fordi de udføres asynkronisk. Som sådan vil langvarige CPU-opgaver blokere hele serveren og er som regel en dårlig ide.

•	Java integrerer godt med relations databaser som MySQL som arbejder ned tabeller. Node.JS + Express gør ikke, da de har mongoDB, fordi mongoDB er et NoSQL database som arbejder med dokumenter og kan nødvendigvis ikke relateres til hinanden.

•	Java modsat Node.JS + Express er et ” stronly typed language”, der giver en vis sikkerhed.

•	500 fejl i Node.JS og Express vil nedbryde (crash) hele applikationen men i Java vil dette ikke ske.

---
## 3. Node.js uses a Single Threaded Non-blocking strategy to handle asynchronous task. Explain strategies to implement a Node.js based server architecture that still could take advantage of a multi-core Server.
---

Node. js kommer ikke med mutlithreading ud af boksen, da det er enkelttrådet, men det er muligt at bygge og programmere det selv. 

 

Som nævnt så eNode.js non-blocking som betyder at alle funktioner (callbacks) er delegeret til et event loop og de er (eller kan være) udført af forskellige tråde i eventloopet og bliver behandlet af Node.js run-time. 

Det kan sammenlignes med er restaurant, hvor en tjener får en ordre fra kunden og giver ordreren videre til overtjeneren, som giver ordren til kokken, som skal udføre ordreren. Når kokken er klar med retten, giver han den til overtjeneren som giver videre til tjeneren, som serverer kunden. På den måde kan overtjeneren håndtere alle tjenerne i stedet for at alle tjenerne venter på kokken. Summa summarum overtjeneren styrer forløbet = som er event-loop.

 

I flowet tager vi udgangspunkt i en Chat, hvor der er 4 personer som skriver til et blad og her er angivet en rækkefølge for hvornår deres skriv/chat kommer ind. Det betyder at inventloopet håndterer rækkefølgen.

For skalering i hele webserviceen, bør du køre flere Node. js servere på en eller flere maskiner/es, en pr kerne og split anmodning trafik mellem dem. Dette giver fremragende CPU-affinitet og vil skalere gennem næsten lineært med Core Count. Du kan også sætte en Load Balancer foran det. Belastningsjusteringen vil afbalancere belastningen af indkommende anmodninger og dermed opnå en multicore-løsning

For skalering overalt på en webservice, skal du køre flere Node.js-servere på en eller flere maskiner/es, en pr. kerne og dele forespørgselstrafik (request traffic) mellem dem. Dette giver fremragende CPU-affinitet (CPU-affinity) og viljestørrelse gennem næsten lineært med kerneantal. Du kan også lægge en belastningsbalancer foran den. Lastbalanceren vil afbalancere belastningen af indgående forespørgsler og dermed opnå en multicore-løsning

---
## 4. Explain briefly how to deploy a Node/Express application including how to solve the following deployment problems:
---

## - Ensure that you Node-process restarts after a (potential) exception that closed the application

## - Ensure that you Node-process restarts after a server (Ubuntu) restart

## - Ensure that you can take advantage of a multi-core system

## - Ensure that you can run “many” node-applications on a single droplet on the same port (80)


---
## 5. Explain the difference between “Debug outputs” and application logging. What’s wrong with console.log(..) statements in our backend-code.
---

---
## 6. Demonstrate a system using application logging and “coloured” debug statements.
---

---
## 7. Explain, using relevant examples, concepts related to testing a REST-API using Node/JavaScript + relevant packages 
---

---
## 8. Explain, using relevant examples, the Express concept; middleware.
---

![billede](https://user-images.githubusercontent.com/32638165/54477713-7ae1c500-480a-11e9-8db1-2903cef2859d.png)

---
## 9. Explain, using relevant examples, how to implement sessions and the legal implications of doing this.
---

---
## 10. Compare the express strategy toward (server side) templating with the one you used with Java on second semester.
---

---
## 11. Demonstrate a simple Server Side Rendering example using a technology of your own choice (pug, EJS, ..).
---

---
## 12. Explain, using relevant examples, your strategy for implementing a REST-API with Node/Express and show how you can "test" all the four CRUD operations programmatically using, for example, the Request package.
---

---
## 13. Explain, using relevant examples, about testing JavaScript code, relevant packages (Mocha etc.) and how to test asynchronous code.
---

---
## 14. Explain, using relevant examples, different ways to mock out databases, HTTP-request etc.
---

---
## 15. Explain, preferably using an example, how you have deployed your node/Express applications, and which of the Express Production best practices you have followed.
---


