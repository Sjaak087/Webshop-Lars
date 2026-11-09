# NovaShop – Firebase webshop

Een responsive webshop in de stijl van een moderne grote webwinkel, gebouwd met HTML/CSS/JavaScript-modules en jouw Firebase-project.

## Inbegrepen
- Productoverzicht, zoeken, productdetail en winkelwagen.
- Firebase Authentication: account maken, inloggen en sessie onthouden.
- Bestellen vereist een account.
- Na een bestelling wordt een chat aangemaakt.
- Klant kan eigen chats, bestellingen en track & trace bekijken.
- Sitebeheer met product toevoegen/bewerken/verwijderen, afbeeldingen uploaden, chats beantwoorden en orderstatus beheren.
- Orderstatussen: ontvangen, verwerkt, gemaakt, klaar voor bezorging.

## 1. Beheer-e-mailadres instellen
Open **firebase.js** en vervang:
`beheer@jouwdomein.nl`
door het e-mailadres dat jij als beheerder wilt gebruiken.

Gebruik exact hetzelfde e-mailadres (bij voorkeur kleine letters) ook in:
- `database.rules.json`
- `storage.rules`

Het wachtwoord zet je bewust **niet** in JavaScript. Alles wat in een website-script staat, kan iedereen bekijken. Maak het beheerdersaccount aan in Firebase Console:
1. Open Firebase Console → jouw project → Authentication.
2. Kies Get started en schakel **Email/Password** in bij Sign-in method.
3. Open Users → Add user.
4. Maak het account aan met het beheer-e-mailadres en een sterk wachtwoord.
5. Gebruik deze gegevens via de knop **Sitebeheer** in de bovenbalk.

**Waarom Firebase Authentication?** Dit is de Firebase-dienst die e-mail/wachtwoordaccounts veilig beheert. De gebruikers kunnen dus in jouw Firebase-project worden teruggevonden onder Authentication → Users. Realtime Database bevat de webshopgegevens (producten, bestellingen en chats). Wachtwoorden worden niet als leesbare tekst in Realtime Database opgeslagen.

Gebruikers kunnen zelf via de webshop een account maken.

## 2. Firebase Database-regels instellen
1. Firebase Console → Realtime Database → Rules.
2. Vervang de bestaande regels door de inhoud van `database.rules.json`.
3. Pas eerst het beheer-e-mailadres aan en klik op Publish.

## 3. Firebase Storage instellen
1. Firebase Console → Storage → Get started.
2. Open Storage → Rules.
3. Vervang de regels door `storage.rules` (pas ook daar het beheer-e-mailadres aan).
4. Klik op Publish.

Productfoto's worden in Firebase Storage opgeslagen. De database bevat de productgegevens en afbeeldings-URL's.

## 4. Analytics
De meegeleverde configuratie bevat je `measurementId`. Analytics is optioneel en is voor deze webshop niet nodig om de winkelwagen, accounts, bestellingen of chats te laten werken.

## 5. Lokaal testen
Omdat de site JavaScript-modules gebruikt, open je `index.html` niet rechtstreeks via `file://`.
Start in de projectmap bijvoorbeeld een lokale server:
- VS Code: installeer de extensie **Live Server** en kies Open with Live Server.
- Of met Python: `python -m http.server 8000` en open `http://localhost:8000`.

## 6. Publiceren via GitHub Pages
1. Maak een nieuwe GitHub-repository.
2. Upload alle bestanden uit deze map naar de hoofdmap van de repository.
3. Ga naar Settings → Pages.
4. Kies Deploy from a branch → `main` → `/ (root)` → Save.
5. Wacht tot GitHub Pages de website publiceert.

## Belangrijke beveiligingsnotities
- De Firebase web-apiKey is een publieke client-key; dat is normaal voor Firebase-webapps. Beveiliging komt uit Authentication en Database-/Storage Rules.
- Zet nooit een admin-wachtwoord, service-account-key of private key in frontendbestanden of GitHub.
- De voorbeeldregels gebruiken een beheerder op basis van het geverifieerde Firebase-login-e-mailadres. De e-mailadressen in alle drie de configuratiebestanden moeten exact overeenkomen.
- De meegeleverde basisregels zijn een startpunt. Voor een echte winkel met betalingen, voorraad, verzendlabels of persoonsgegevens is aanvullende server-side validatie nodig. Er is geen online betaalprovider aangesloten.
- Test na het publiceren altijd met een normaal klantaccount én met het beheerdersaccount.

## Waarom staat het beheerderswachtwoord niet in een script?
Een wachtwoord in `firebase.js` of `app.js` is zichtbaar voor iedereen die de GitHub-pagina opent. Daarom staat alleen het beheer-e-mailadres in de configuratie; het wachtwoord stel je in bij Firebase Authentication. De knop Sitebeheer staat nu in de bovenste navigatiebalk.

Wil je per se geen Firebase Authentication gebruiken, dan is een beveiligde server (bijvoorbeeld Firebase Cloud Functions) nodig om wachtwoorden veilig te controleren. Alleen Realtime Database + browser-JavaScript is geen veilige manier om accounts en bestellingen af te schermen. Sla nooit gewone wachtwoorden op in de database.
