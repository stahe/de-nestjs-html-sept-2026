# Eine Webanwendung mit dem Framework NestJS erstellen

📖 **Das Tutorial lesen: [https://stahe.github.io/de-nestjs-html-sept-2026/](https://stahe.github.io/de-nestjs-html-sept-2026/)**

Dieser Kurs zeigt, wie man mit dem Framework [NestJS](https://nestjs.com) eine **MVC**-Webanwendung erstellt: eine Anwendung, deren HTML-Seiten **vom Server** mit der View-Engine Handlebars erzeugt werden, ohne ein clientseitiges JavaScript-Framework.

Er folgt dem Aufbau des Kurses [Einführung in ASP.NET MVC anhand von Beispielen](https://stahe.github.io/de-aspnetmvc-nov-2013/) (2013), übertragen auf das Node.js/TypeScript-Ökosystem:

| ASP.NET MVC (2013) | NestJS (2026) |
|---|---|
| C#, Controller, Actions | TypeScript, `@Controller`, `@Get`, `@Post` |
| Razor-Views, `_Layout.cshtml` | Handlebars-Views, `layout.hbs` |
| `[Required]`, `ModelState.IsValid` | class-validator, Formularvalidierung |
| Session, `TempData` | Cookies, JWT-Token, Flash-Meldungen |
| Filter, `[Authorize]` | Middleware, Guards, Interceptors, `@Roles` |
| Entity Framework | TypeORM + MySQL |

## Der Ansatz: viele kurze Beispiele, dann eine Fallstudie

Der Kurs besteht aus **28 kurzen Projekten**, die sich jeweils auf ein einziges Konzept konzentrieren. Sie lassen sich ausführen und verändern. Alle Beispiele teilen sich ein einziges `npm install`.

| Kapitel | Inhalt | Beispiele |
|---|---|---|
| Controller, Actions, Routing | Routen, Antworten, Weiterleitungen, Module, Dependency Injection | 01–06 |
| Das Action-Modell | Parameter, Konvertierung, Validierung, POST-Formulare, Pipes | 07–12 |
| Die View und ihr Template | Handlebars, Templates, Partials, Helper, Formulare, Validierung, Post/Redirect/Get, Bestätigungsdialog | 13–21 |
| Internationalisierung | Eine Anwendung auf Französisch und Englisch | 22 |
| Datenbereiche | Anwendung, Request, Client | 23 |
| Der Lebenszyklus einer Anfrage | Middleware, Guard, Interceptor, Pipe, Exception-Filter | 24 |
| Authentifizierung und Autorisierung | JWT in einem Cookie, Rollen, CAPTCHA, Rate Limiting | 25 bis 27 |
| Schichtenarchitektur | Web / Geschäftslogik / DAO mit TypeORM, Transaktionen, optimistisches Sperren | 28 |

Jedes Beispiel wird mit seinem vollständigen Code und zeilenweisen Kommentaren vorgestellt. Der Kurs zeigt auch die Ergebnisse zur Laufzeit: Browser-Screenshots, mit `curl` erhaltene rohe HTTP-Antworten und Server-Logs.

## Die Fallstudie: RdvMedecins

Die Fallstudie ist eine vollständige Anwendung zur **Terminplanung in einer Arztpraxis**. Sie besteht aus etwa sechzig Dateien, die **alle** aufgelistet und kommentiert werden. Sie führt alle in den vorherigen Kapiteln behandelten Konzepte zusammen.

- **Drei Rollen:**
  - `ADMIN` verwaltet Ärzte und Kunden;
  - `DOCTOR` bucht und storniert Termine;
  - `USER` ist der Patient: Er bucht Termine für sich selbst und verwaltet sein Konto.
- **Geschäftsregeln:**
  - keine Termine in der Vergangenheit;
  - nur ein bevorstehender Termin pro Patient;
  - keine doppelten Namen dank benannter Eindeutigkeitsbedingungen;
  - eine optimistische Sperre verhindert das Überschreiben eines Datensatzes, der zwischenzeitlich von einem anderen Benutzer geändert wurde.
- **Datenschutz:** Ein Patient sieht nie die Namen anderer Patienten. Dieser Name wird nicht einmal an seinen Browser gesendet.
- **Sicherheit:**
  - JWT-Token in einem `httpOnly`- / `sameSite`-Cookie;
  - mit bcrypt gehashte Passwörter;
  - CAPTCHA und vorübergehende Sperre nach mehreren fehlgeschlagenen Anmeldeversuchen;
  - durch einen einmal verwendbaren „Passcode“ geschützte Kontoerstellung.
- **Eine zweisprachige Oberfläche** (Französisch/Englisch), erstellt mit Bootstrap 5.
- **Progressive Enhancement:** Die Anwendung funktioniert vollständig ohne JavaScript. Ein kleines Skript ergänzt lediglich einen per Tastatur bedienbaren Bestätigungsdialog.

## Technologien

NestJS 10 · TypeScript 5 · Express · Handlebars (hbs) · class-validator / class-transformer · TypeORM · MySQL 8 / MariaDB · Passport JWT · bcrypt · svg-captcha · Bootstrap 5

## Voraussetzungen

- Grundkenntnisse in TypeScript (oder JavaScript), HTML und im HTTP-Protokoll.
- Node.js 20 oder neuer, Visual Studio Code und ein MySQL-Server (z. B. Laragon unter Windows). Installationsanleitungen finden sich in den Anhängen des Kurses.

## Autor

Dieser Kurs, seine Beispiele und seine Fallstudie wurden von **Claude**, der KI von [Anthropic](https://www.anthropic.com), geschrieben (September 2026).
