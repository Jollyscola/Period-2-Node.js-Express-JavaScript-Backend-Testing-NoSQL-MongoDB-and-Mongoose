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

---
## 17. Explain Pros & Cons in using a NoSQL database like MongoDB as your data store, compared to a traditional Relational SQL Database like MySQL.
---

---
## 18. Explain reasons to add a layer like Mongoose, on top on of a schema-less database like MongoDB
---

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

---
## 23. Demonstrate, using your own code-samples, decisions you have made regarding → normalization vs denormalization 
---

---
## 24. Explain, using a relevant example, a full JavaScript backend including relevant test cases to test the REST-API (not on the production database)
---






