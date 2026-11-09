# NovaShop

## Accounts en beheerder
- Firebase Authentication controleert veilig de e-mailadressen en wachtwoorden.
- Accountprofielen worden opgeslagen in Realtime Database onder `users/{uid}` met e-mailadres, aanmaakdatum en accounttype.
- Wachtwoorden worden bewust NIET opgeslagen in Realtime Database of in openbare JavaScript-bestanden.
- Maak het beheerdersaccount aan via Firebase Console > Authentication > Users.
- Zet het e-mailadres daarvan in `beheer-config.js` bij `adminEmail`.
- Open Sitebeheer en log in met het e-mailadres en wachtwoord van dat Firebase Authentication-account.

## Firebase instellen
1. Controleer `firebase.js`.
2. Publiceer `database.rules.json` in Firebase Realtime Database.
3. Publiceer `storage.rules` in Firebase Storage.
4. Schakel E-mail/wachtwoord in via Firebase Console > Authentication > Sign-in method.

De Firebase webconfiguratie en `beheer-config.js` zijn zichtbaar voor bezoekers van een statische website. Plaats daar nooit wachtwoorden of geheime sleutels in. De beveiliging wordt afgedwongen met Firebase Authentication en Firebase-regels.
