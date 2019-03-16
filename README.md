# Period-2-Node.js-Express-JavaScript-Backend-Testing-NoSQL-MongoDB-and-Mongoose
---
## Why would you consider a Scripting Language as JavaScript as your Backend Platform?
---

• Det er nemt og hurtigt, at opbygge og opsætte et arbejdsnetværksprogram (a working network application) med node.js og den rigtige editor.

• Det er meget praktisk, at du kan bruge det samme sprog både i front-end og i back-end.

• Der kræves ikke meget kode for, at en applikation kan køre.


---
## Explain Pros & Cons in using Node.js + Express to implement your Backend compared to a strategy using, for example, Java/JAX-RS/Tomcat

---

PROS
•	Man kan lave en hurtig response network application, hvis det er gjort rigtigt. 

•	Tillader at sende filer hurtigt igennem datastreaming og hurtige filoverførsler (file uploads). 

•	Det er nemt at opsætte en REST-API med Express application generator som et brugerdefineret standardprojekt, Express. 


Først install node.js https://nodejs.org/en/
bagefter install.
https://expressjs.com/en/starter/installing.html her guide 
```
npm install express -g
```
hvad navn på expres projektet skal hedde.
```
express Navnpåprojektet
cd Navnpåprojektet
npm install
npm start 
```
Så er man hurtigt i gang med express projekt. 

•	Det er effektivt at håndtere tusindvis af samtidige anmodninger (for eksempel-en chat applikation). 

•	Det er meget simpelt at implementere server middleware, der vil blive udført imellem alle request (hvis requerment er tilladt).

CONS
•	Java er god til at håndtere CPU-tunge opgaver, Node.JS + Express er ikke. Fordi Node er, på trods af sin asynkronhændelsesmodel, af 
natur enkelttrådet. Når du starter en Node-proces, kører du en enkelt proces med en enkelt tråd på en enkelt kerne. Så din kode vil ikke blive udført parallelt, kun I/O-operationer er parallelle, fordi de udføres asynkronisk. Som sådan vil langvarige CPU-opgaver blokere hele serveren og er som regel en dårlig ide.

•	Java integrerer godt med relations databaser som MySQL som arbejder ned tabeller. Node.JS + Express gør ikke, da de har mongoDB, fordi mongoDB er et NoSQL database som arbejder med dokumenter og kan nødvendigvis ikke relateres til hinanden.

•	Java modsat Node.JS + Express er et ” stronly typed language”, der giver en vis sikkerhed.

•	500 fejl i Node.JS og Express vil nedbryde (crash) hele applikationen men i Java vil dette ikke ske.

---
## Node.js uses a Single Threaded Non-blocking strategy to handle asynchronous task. Explain strategies to implement a Node.js based server architecture that still could take advantage of a multi-core Server.
---




![billede](https://user-images.githubusercontent.com/32638165/54477713-7ae1c500-480a-11e9-8db1-2903cef2859d.png)
