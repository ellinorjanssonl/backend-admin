Backend Admin Server
Denna backend-server är designad för att hantera GDPR-förfrågningar och CSRF-säkerhet samt
JWT-verifiering för en säker användarupplevelse.
## Innehåll

- [Installation](#installation)
- [Konfiguration](#konfiguration)
- [API Endpoints](#api-endpoints)
- [Funktioner](#funktioner)
- [Teknologier](#teknologier)
- [Starta servern](#starta-servern)

## Installation
1. Klona detta repo:
 ´´´bash
 git clone <repo-url>
 cd <repo-namn>

2. Installera beroenden:
´´´bash
 npm install

3. Skapa en `.env`-fil i rotkatalogen med följande variabler:

 DB_HOST=<your-database-host>
 DB_USER=<your-database-user>
 DB_PASSWORD=<your-database-password>
 DB_DATABASE=<your-database-name>
 DB_PORT=<your-database-port>
 PORT=<server-port>

## Konfiguration
- connectDB.js: Anslutningen till MySQL-databasen är konfigurerad med hjälp av miljövariabler
definierade i `.env`-filen.

## API Endpoints
### GDPR Endpoints
Dessa endpoints används för att hantera användares GDPR-förfrågningar.

- GET /gdpr/request-data: Hämtar användarens data inklusive uppgifter, uppgifter de är tilldelade,
och kommentarer. Kräver CSRF-token och JWT-verifiering.

- DELETE /gdpr/request-delete: Tar bort användarens konto och relaterad data. Kräver CSRF-token
och JWT-verifiering.

### CSRF Endpoint
CSRF-säkerhet hanteras genom följande endpoint:

- GET /token: Genererar en CSRF-token för användaren. Kräver JWT-verifiering.

## Funktioner
- GDPR-stöd: Möjlighet att hämta och ta bort användarens data från databasen. Transaktioner
hanteras för att säkerställa data-integritet.
- CSRF-skydd: Token genereras och verifieras för att skydda mot CSRF-attacker.
- JWT-verifiering: JWT används för att säkra endpoints. Verifieringen sker genom en extern
auth-server som kontrollerar token-validiteten.

## Teknologier
- Node.js och Express: För server- och API-hantering.
- MySQL: Som databas, hanterad genom `mysql2/promise`.
- dotenv: För hantering av miljövariabler.
- helmet och cors: För säkerhet och hantering av CORS-policyer.

## Starta servern
Kör följande kommando för att starta servern:
 npm start
Servern kommer att köras på den port som definieras i `.env`-filen eller på `3002` som standard.
