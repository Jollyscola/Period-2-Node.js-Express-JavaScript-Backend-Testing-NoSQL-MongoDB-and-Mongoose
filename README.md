# Period-2-Node.js-Express-JavaScript-Backend-Testing-NoSQL-MongoDB-and-Mongoose
---
## 1. Why would you consider a Scripting Language as JavaScript as your Backend Platform?
---

Grunden til at Node.js er rigtigt godt er, fordi de udvikler og hjælper til at løse problemer for dem der programmerer. 
JavaScript er et rigtigt godt værktøj for serveren, med følgende grunde:


•	Det er nemt og hurtigt, at opbygge og opsætte et arbejdsnetværksprogram (a working network application) med node.js og den rigtige editor.

•	Det er meget praktisk, at du kan bruge det samme sprog både i front-end og i back-end.

•	Der kræves ikke meget kode for, at en applikation kan køre.


Der er flere back-end sprog men JavaScript er helt sikkert et sprog man skal overveje at bruge som virksomhed.


---
## 2. Explain Pros & Cons in using Node.js + Express to implement your Backend compared to a strategy using, for example, Java/JAX-RS/Tomcat

---

### PROS
•	Man kan lave en hurtig response network application, hvis det er gjort rigtigt. 

•	Tillader at sende filer hurtigt igennem datastreaming og hurtige filoverførsler (file uploads). 

•	Det er nemt at opsætte en REST-API med Express application generator som et brugerdefineret standardprojekt, Express. 

•	Det er effektivt at håndtere tusindvis af samtidige anmodninger (for eksempel-en chat applikation). 

•	Det er meget simpelt at implementere server middleware, der vil blive udført imellem alle request (hvis requerment er tilladt).

#### En lille guide til express projekt 

Først install man node.js https://nodejs.org/en/

Bagefter i sin terminal skrive man denne kommentar. 
```
npm install express -g
```

Sådan start man expres projektet op.
```
express Navnpåprojektet
cd Navnpåprojektet
npm install
npm start 
```
og til sidst skrive det i din browser "localhost:3000/"

![Exprestfirstformit](https://user-images.githubusercontent.com/32638165/54492293-7af2cb00-48c5-11e9-9c6e-f84190c09ef5.JPG)

Så er man hurtigt i gang med express projekt. 

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

![billede](https://user-images.githubusercontent.com/32638165/54491851-ecc91580-48c1-11e9-84a2-91aae826ce78.png)


Som nævnt så eNode.js non-blocking som betyder at alle funktioner (callbacks) er delegeret til et event loop og de er (eller kan være) udført af forskellige tråde i eventloopet og bliver behandlet af Node.js run-time. 

Det kan sammenlignes med er restaurant, hvor en tjener får en ordre fra kunden og giver ordreren videre til overtjeneren, som giver ordren til kokken, som skal udføre ordreren. Når kokken er klar med retten, giver han den til overtjeneren som giver videre til tjeneren, som serverer kunden. På den måde kan overtjeneren håndtere alle tjenerne i stedet for at alle tjenerne venter på kokken. Summa summarum overtjeneren styrer forløbet = som er event-loop.

![billede](https://user-images.githubusercontent.com/32638165/54491854-f5215080-48c1-11e9-890a-a3b7a788fafb.png) 

I flowet tager vi udgangspunkt i en Chat, hvor der er 4 personer som skriver til et blad og her er angivet en rækkefølge for hvornår deres skriv/chat kommer ind. Det betyder at inventloopet håndterer rækkefølgen.

For skalering i hele webserviceen, bør du køre flere Node. js servere på en eller flere maskiner/es, en pr kerne og split anmodning trafik mellem dem. Dette giver fremragende CPU-affinitet og vil skalere gennem næsten lineært med Core Count. Du kan også sætte en Load Balancer foran det. Belastningsjusteringen vil afbalancere belastningen af indkommende anmodninger og dermed opnå en multicore-løsning.

---
## 4. Explain briefly how to deploy a Node/Express application including how to solve the following deployment problems:
---

## - Ensure that you Node-process restarts after a (potential) exception that closed the application

I produktionen, må applikationen ikke på noget tidspunkt være offline. Det betyder, at du skal sørge for, at den genstarter både, hvis appen går ned, og hvis serveren selv går ned. Forhåbningsvis vil ingen af disse begivenhederne forekomme, ellers skal du tage højde for begge eventualiteter, ved følgende:

•	Ved hjælp af en ”Process Manager” som genstarter app’en (og node), når den går ned.

• Ved hjælp af init system, leveret af dit operativsystem til at genstarte ”Process Manager”, når OS går ned. 

•	Det er også muligt at bruge init-systemet uden en ”Proces Manager”. Node applikationen går ned, hvis den støder på en uopdaget undtagelse. 

Det er vigtigt at sikre, at app’en er velafprøvet og håndterer alle undtagelser. Men som en sikkerhed mod fejl, skal der sættes en mekanisme ind for at sikre, at hvis og når din app går ned, vil den automatisk genstarte.

## - Ensure that you Node-process restarts after a server (Ubuntu) restart


Det næste er at sikre, at din app genstarter, når serveren genstarter. Systemer kan stadig gå ned af forskellige årsager. For at sikre, at din app genstarter, hvis serveren går ned, skal du bruge init-systemet indbygget i dit operativsystem (OS). De to vigtigste init-systemer i brug i dag er ”systemd” og ”Upstart”. 

Der er to måder at bruge init-systemer med din Express-app: 

1.	Kør din app i en proces manager og installer process manager som en tjeneste med init-systemet. Process manager’en vil restarte app’en, når app’en krakker og init-systemet vil restart den process manager, når OS restarter. Dette er den anbefalede fremgangsmåde. 

2.	Kør din app (og node) direkte med init-systemet. Dette er noget enklere, men du får ikke de yderligere fordele, som man får ved at bruge en process manager.

## - Ensure that you can take advantage of a multi-core system

En enkelt forekomst af Node.js kører i en enkelt tråd. For at drage fordel af multi-core-systemer, vil brugeren nogle gange ønske, at lancere en klynge af Node.js processer til at håndtere belastningen. Klynge modulet (The cluster module) gør det nemt at oprette underordnede processer, som alle deler server porte

exemple: 

```javascript
const cluster = require('cluster')
const http = require('http')
const numCPUs = require('os').cpus().length;
if (cluster.isMaster) {
console.log(`Master ${process.pid} is running`);
// Fork workers.
for (let i = 0; i < numCPUs; i++) {
cluster.fork()
}
cluster.on('exit', (worker, code, signal) => {
console.log(`worker ${worker.process.pid} died`)
})
} else {
// Workers can share any TCP connection
// In this case it is an HTTP server
http.createServer((req, res) => {
res.writeHead(200)
res.end('hello world\n')
}).listen(8000)
console.log(`Worker ${process.pid} started`)
}
```


## - Ensure that you can run “many” node-applications on a single droplet on the same port (80)

Dette kan opnås ved at implementere en ”reversy proxy” dvs. Nginx Ref: hosting flere apps på, ref.: 
Hosting Multiple Apps on the same Server — Implement a Reverse Proxy with Node

---
## 5. Explain the difference between “Debug outputs” and application logging. What’s wrong with console.log(..) statements in our backend-code.
---

---
## 6. Demonstrate a system using application logging and “coloured” debug statements.
---

Igennem debug statements er det vigtigt man kigger på, hvad der sker i udviklingen af indholdet i forløbet

Ved at install det her.

```
npm install debug --save
```

Kan man debug ens side ved f.eks skrive 

```
debug node.js hvilketprojetmanvildebug
```

index.js
```javascript
var express = require('express');
var router = express.Router();


var model = {
  title: "Site with a simple JOKE API",
  howToUse: "Get a random joke like this: /api/random"

}
/* GET home page. */
router.get('/', function(req, res, next) {
  res.render('index', { title: model.howToUse });
});

module.exports = router;
```

Her se man hvordan programmeringen af index.js side 

```javascript
1 (function ( "exports", require, module, __filename, __dirname) { var express = require('express');
  2 var router = express.Router();
  3
debug> n
> 1 (function (exports, require, module, __filename, __dirname) { var express = "require"('express');
  2 var router = express.Router();
  3
debug> n
  1 (function (exports, require, module, __filename, __dirname) { var express = require('express');
> 2 var router = express."Router()";
  3
  4
debug> n
  3
  4
> 5 var model = "{"
  6   title: "Site with a simple JOKE API",
  7   howToUse: "Get a random joke like this: /api/random"
debug> n
  9 }
 10 /* GET home page. */
>11 router."get"('/', function(req, res, next) {
 12   res.render('index', { title: model.howToUse });
 13 });
debug> n
 13 });
 14
>15 "module".exports = router;
 16
 17 });
```
n betyder "next" command. 




---
## 7. Explain, using relevant examples, concepts related to testing a REST-API using Node/JavaScript + relevant packages 
---

Man kan teste ens kode ved mocha og bruge chai, expert til at tjekket om resultet er korret.

```javascript
describe("test af et api", function () {
    before(function (done) {
        apicalcualtor.calcualtorapi(PORT, function (server) {
            serverapi = server;
            done();
        });
    });
    it("8 + 4 = 12", async function () {
        const resurl = await fetch(`${URL}/add/8/4`)
        .then(r => r.text());
        result = Number(resurl);

        expect(result).to.be.equal(12);
    });
    after(function () {
        serverapi.close();
    });
});

```

---
## 8. Explain, using relevant examples, the Express concept; middleware.
---

En Express-applikation er i det væsentlige en stak middleware, der udføres i en pipeline/rækkefølge (serially). En middleware er en funktion med adgang til request object (reg), responsobjektet (res) og den næste middleware i rækken i the request-response cycle af en Express application.

Hver middleware har evnen til at udføre koder, foretage ændringer i request og the response object, afslutte the request-response cycle, og kalde det næste middleware i stakken. Da middleware udføres serielt (serially), er deres rækkefølge af inddragelse vigtig.

Hvis det nuværende middleware ikke afslutter the request-response cyklussen, er det vigtigt at kalde next() for at videregive kontrollen til næste middleware ellers vil the request forblive hængende.

Request Flow jf. som skitseret nedenfor: 

![billede](https://user-images.githubusercontent.com/32638165/54493147-d4122d00-48cc-11e9-8605-53f0a0cf9ce4.png)

#### Middleware: http://expressjs.com/en/guide/using-middleware.html 
 
I en Express Application er der et enkelt single-entry point for alle requests, der kommer til the app - via app.js. Når en HTTP-request (anmodning) ankommer til vores app, går den igennem stakken af middleware.


Eksempel: 

``` javascript
const express = require('express')
const app = express()
const port = 3002

app.use("/", function (req, res, next) {
    console.log("Request was made " + req.ip);
    next();
});

app.get('/', function (req, res) {
    res.send('Hello World!')
});

app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```

Output
```
Example app listening on port 3002!
Request was made ::1
```

---
## 9. Explain, using relevant examples, how to implement sessions and the legal implications of doing this.
---

HTTP er stateles og har ungen rettigheder. For at forbinde en request til en anden request, har du brug for en måde at gemme userens/brugerens data mellem HTTP request’s. Cookies ag URL parametre er begge egnede måder at transportere data mellem klienten og serveren. De er både læsbare og på the client siden. Du tildeler the client et ID og alle fremtidige request vil bruge dette ID. Informationer tilknyttet the client gemmes på serveren, der knyttes til dette ID.

Install express-session gør at man kan køre denne pakke.

```
npm install express-session
```

##### Session

```javascript
var express = require('express');
var session = require('express-session');

var app = express();

app.use(session({secret: "Shh, its a secret!"}));

app.get('/', function(req, res){
   if(req.session.page_views){
      req.session.page_views++;
      res.send("You visited this page " + req.session.page_views + " times");
   } else {
      req.session.page_views = 1;
      res.send("Welcome to this page for the first time!");
   }
});
app.listen(3000);
```
Output

![billede](https://user-images.githubusercontent.com/32638165/54496930-1e0f0900-48f5-11e9-952e-bbdb821a2d66.png)


---
## 10. Compare the express strategy toward (server side) templating with the one you used with Java on second semester.
---

Node.JS og Express bruger ”templating engines” som ”Handlebars”, Jade og EJS. Java bruger ”templating engines” som JSP. Java blev aldrig lavet til at være egnet til web-applikationer og JSP ses ofte som en provisorisk løsning.

•	Java: Model --> Controller --> Servlet --> JSP

•	Express.js: Model --> Controller/Router --> Handlebars/Jade/EJS

Example 1 (Passing variables to a view in Express)
Node.js + Express.js:

```javascript
router.get('/dashboard', isLoggedIn, function (req, res) {
    res.render('dashboard', {
        title: 'Dashboard',
        subtitle: 'Hello dashboard'
    });
});
```

Java + JSP

```java
protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        RequestDispatcher rd = null;
        HttpSession session = request.getSession();
        session.setMaxInactiveInterval(30 * 60);

        session.setAttribute("title", "Dashboard");
        session.setAttribute("subtitle", "Hello dashboard");
        rd = request.getRequestDispatcher("dashboard.jsp");
        rd.forward(request, response);

}
```

Example 2 (Retrieving a session variable on the front end with Handlebars)

Node.js + Express.js:
```javascript 
<h1>{{title}}</h1>
<h2>{{subtitle}}</h2>
```
Java + JSP
```java
<h1><%= session.getAttribute("title"); %></h1>
<h2><%= session.getAttribute("subtitle"); %></h2>
```
---
## 11. Demonstrate a simple Server Side Rendering example using a technology of your own choice (pug, EJS, ..).
---

---
## 12. Explain, using relevant examples, your strategy for implementing a REST-API with Node/Express and show how you can "test" all the four CRUD operations programmatically using, for example, the Request package.
---

---
## 13. Explain, using relevant examples, about testing JavaScript code, relevant packages (Mocha etc.) and how to test asynchronous code.
---

Mocha er en test struktur, der kører på node.js og kan bruges til at teste synkrone og asynkrone funktioner. Mocha tests kører serielt og giver mulighed for fleksibel og præcis rapportering, mens kortlægning af ufangede undtagelser til de korrekte test tilfælde. -> "describe" + "it".

Chai er en BDD/TDD (Behavior-/Test-Driven Development) påstand (assertion) bibliotek for node og browseren, der kan parres med enhver JavaScript test Framework. -> "should" + "expect" + "assert". request: Anmodning (request) er designet til at være den enkleste måde at foretage http-opkald (calls). Det understøtter HTTPS og følger omdirigeringer som standard.


```javascript 
//var expect = require("chai").expect;
const {expect} = require("chai"); //es6 way of doing it

describe("Testing async behaviour", function () {
    var foo = false;
    before(function (done) { //done callback
        setTimeout(function () {
            foo = true
            done(); // test fails without this
        }, 1000);
    });

    it("should pass (with done called)", function () {
        expect(foo).to.equal(true);
    })
})
```
Testing the indexOf method on an array with 3 values:
```javascript
var assert = require('chai').assert;
describe('Array', function() {
  describe('#indexOf()', function () {
    it('should return -1 when the value is not present', function () {
      assert.equal(-1, [1,2,3].indexOf(5));
      assert.equal(-1, [1,2,3].indexOf(0));
    });
  });
});

```
Working with hooks:
With its default “BDD”-style interface, Mocha provides the hooks before(), after(), beforeEach(), and afterEach(). These should be used to set up preconditions and clean up after your tests.

```javascript
describe('hooks', function() {

  before(function() {
    // runs before all tests in this block
  });

  after(function() {
    // runs after all tests in this block
  });

  beforeEach(function() {
    // runs before each test in this block
  });

  afterEach(function() {
    // runs after each test in this block
  });

  // test cases
});
```

---
## 14. Explain, using relevant examples, different ways to mock out databases, HTTP-request etc.
---

---
## 15. Explain, preferably using an example, how you have deployed your node/Express applications, and which of the Express Production best practices you have followed.
---


# NoSQL, MongoDB and Mongoose

---
## 16. Explain, generally, what is meant by a NoSQL database.
---


NoSQL er et udtryk, der refererer til en bestemt type databasemodel eller database management system (DBMS). NoSQL er et meget bredt begreb, der ikke refererer til en bestemt databasemodel. Det refererer snarere til en lang række forskellige modeller, der ikke passer ind i relationsmodellen.
NoSQL database er en mekanisme til lagring og hentning af data, der er modelleret på andre måder end de tabelrelationer, der anvendes i relationelle databaser (relational databases). NoSQL databaser anvendes i stigende grad ved store datamængder og i realtid web-applikationer. 
NoSQL omfatter en bred vifte af forskellige database teknologier, der blev udviklet som svar på de krav, der præsenteres i opbygningen af moderne applikationer: 

•	Udviklere arbejder med applikationer, der skaber massive mængder af nye, hurtigt skiftende data typer — strukturerede, semistrukturerede, ustrukturerede og polymorfe data.

•	”Long gone” er den tolv-til-atten måneders vandfald udvikling cyklus. Nu arbejder små teams i agile sprints, itererating hurtigt og skubber kode hver uge eller to, nogle endda flere gange hver dag. 

•	Applikationer, der engang tjente et endeligt publikum, leveres nu som tjenester, der altid skal være tilgængelige fra mange forskellige enheder og skaleres globalt til millioner af brugere.

•	Organisationer henvender sig nu til skaleringsbaserede arkitekturer ved hjælp af open source-software, commodity servere og cloud-computing i stedet for store monolitiske servere og storage-infrastruktur. 

Relationelle databaser var ikke designet til at klare den skala og agility udfordringer, man står over for i moderne applikationer. De var heller ikke bygget til at drage fordel af den ”commodity servers” og ”processing power” som er til rådighed i dag. 

---
## 17. Explain Pros & Cons in using a NoSQL database like MongoDB as your data store, compared to a traditional Relational SQL Database like MySQL.
---

Højdepunkter SQK vs NoSQL

|SQL|NoSQL|
|---|----|
|RELATIONAL DATABASE MANAGEMENT SYSTEM (RDBMS)|Non-relational or distributed database system.|
|These databases have fixed or static or predefined schema|They have have dynamic schema|
|These databases are not suited for hierarchical data storage.|These databases are best suited for hierarchical data storage.|
|These databases are best suited for complex queries|These databases are not so good for complex queries |
|Verticlly Scalable|Horizontally scalable|


Pros & Cons – Sammenligning af MySQL og MongoDB (NoSQL Database)

|Tekst |MySQL|MongoDB|NoSQL Data Store|
|-------|----|---|---|
|Open source|Yes|Yes|Yes|
|ACID Transactions|Yes|Yes|No|
|Fleksibel avanceret datamodel (Flexible, rich data model)|No|Yes| Partial: schema flexibility but support for only simple data structures.|
|Skemastyring (Schema governance)|Yes|Yes|No|
|Expressive joins, faceted search, graphs queries, powerful aggregations|Yes|Yes|No|
|Idiomatic, native language drivers|No|Yes|No|
|Horizontal scale-out with data locality controls|No|Yes|Partial: no controls over data locality.|
|Analytics and BI ready|Yes|Yes|No|
|Enterprise grade security and mature management tools|Yes|Yes|No|
|Database as a service on all major clouds|Yes|Yes|No|







---
## 18. Explain reasons to add a layer like Mongoose, on top on of a schema-less database like MongoDB
---

Mongoose er et objekt dokument modellering (ODM) lag, der sidder på toppen af Node's MongoDB driver. Hvis du kommer fra SQL, svarer det til en ORM for en relationsdatabase. Selv om det ikke er nødvendigt at bruge Mongoose med Mongo, er her fire grunde til at bruge Mongoose med MongoDB: 

1.	Skemaer (Schemas) 
MongoDB er en ”de-normaliseret NoSQL” database. Dette gør det (i sagens natur), at det som dokument er skema-løs med varierende sæt af felter med forskellige datatyper. Selvom dette giver din datamodel fleksibilitet, når den udvikler sig over tid, kan det være svært at håndtere med en SQL-baggrund. Mongoose definerer et skema til dine datamodeller, så dine dokumenter følger en specifik struktur med foruddefinerede datatyper. 

2.	Validering (Validation) 
Mongoose har indbygget validering for skema definitioner. Dette sparer dig for at skrive en masse valideringskoder, som du ellers skulle skrive med MongoDB-driveren. Ved blot at inkludere ting som ”required: true” i dine skemadefinitioner, giver Mongoose out-of-the-box valideringer for dine samlinger (herunder datatyper). 

3.	Instansmetoder (Instance Methods)
Mongoose tilbyder valgfri præ- og post-save-operationer til datamodeller. Dette gør det nemt at definere kroge og brugerdefineret funktionalitet på vellykket læsning/skrivning osv. Man kan også definere brugerdefinerede metoder, der virker på en bestemt instans/forekomst (eller et dokument). Mens du kan opnå lignende funktionalitet med den indfødte MongoDB-driver, gør Mongoose det nemmere at definere og organisere sådanne metoder i din skemadefinition.

4.	Tilbagevendende resultater (Returning results)
Mongoose gør det lettere at returnere opdaterede dokumenter eller søge resultater. Et godt eksempel kan findes med opdateringsforespørgsler. Mens den indbyggede/oprindelige driver returnerer et objekt med et succesflag og antallet af ændrede dokumenter, returnerer Mongoose selve det opdaterede objekt, så du nemt kan arbejde med resultaterne.

Grunde til ikke at bruge Mongoose?
Der er få grunde til ikke at bruge Mongoose med MongoDB (især hvis du lige er begyndt). For mere avancerede forespørgsler, kan det hævdes, at Mongoose gør tingene vanskeligere og kan bremse ydeevnen. Fortalere for den MongoDB-driver hævder desuden, at den bringer ODM til et de-normaliseret design, og derved helt forkaster formålet med en NoSQL-database.


Konklusion
På trods af argumenterne mod at bruge Mongoose forbliver det et af de mest populære ODM-værktøjer til Mongo. Hvis du kommer fra en SQL-baggrund, så bruger Mongoose overgangen til et NoSQL-miljø meget lettere. Det vil også spare dig tid til at skrive egne valideringer og instansmetoder og anbefales stærkt til mindre DB'er og grundlæggende Mongo-operationer.


---
## 19. These two topics will be introduced in period-3
---

### •	Explain about indexes in MongoDB, how to create them, and demonstrate how you have used them.

### •	Explain, using your own code examples, how you have used some of MongoDB's "special" indexes like TTL and 2dsphere


---
## 20. Demonstrate, using a REST-API you have designed, how to perform all CRUD operations on a MongoDB
---

---
## 21. Explain the benefits of using Mongoose, and demonstrate, using your own code, an example involving all CRUD operations
---

---
## 22. Explain the “6 Rules of Thumb: Your Guide Through the Rainbow” as to how and when you would use normalization vs. denormalization.
---

Tommelfingerregler: din guide gennem regnbuen.
Her er nogle "tommelfinger regler" til at guide dig gennem disse ”in-denumberable” (men ikke uendelige) valg:

1.	én: favor indlejring, medmindre der er en tvingende grund til ikke at. 

2.	to: behov for at få adgang til et objekt på egen hånd er en overbevisende grund til ikke at indlejre det.

3.	tre: arrays bør ikke vokse uden bundet. Hvis der er mere end et par hundrede dokumenter på "mange" side, ikke indlejre dem; Hvis der er mere end et par tusinde dokumenter på "mange"-siden, skal du ikke bruge en matrix af ObjectID-referencer. Arrays med høj kardinalitet er en tvingende grund til ikke at indlejre. 

4.	Fire: du skal ikke være bange for joinforbindelser på programniveau: Hvis du indekserer korrekt og bruger projektionsangivelsen (som vist i del 2), er joinforbindelser på programniveau næppe dyrere end server side- join-forbindelser i en relations database. 

5.	Fem: Overvej skrive/læse forholdet, når denormaliceing. Et felt, der for det meste vil blive læst og kun sjældent opdateret er en god kandidat til denormalisering: Hvis du demoraliser et felt, der opdateres ofte så det ekstra arbejde med at finde og opdatere alle forekomster er tilbøjelige til at overvælde de besparelser, du får fra denormaliserende. 

6.	Seks: som altid med MongoDB, hvordan du modellerer dine data afhænger – helt – på din særlige applikationsdata adgangs mønstre. Du vil strukturere dine data, så de passer til de måder, som dit program forespørger på og opdaterer det.

---
## 23. Demonstrate, using your own code-samples, decisions you have made regarding → normalization vs denormalization 
---

---
## 24. Explain, using a relevant example, a full JavaScript backend including relevant test cases to test the REST-API (not on the production database)
---






