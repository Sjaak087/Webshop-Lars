# NovaShop - demo zonder Firebase Authentication

Deze demo gebruikt **Firebase Realtime Database**. Firebase Authentication wordt niet meer gebruikt.

## Sitebeheer demo-inlog
- E-mail: beheer@jouwdomein.nl
- Wachtwoord: NovaShop123!

Pas deze gegevens aan in `beheer-config.js`.

## Klantenaccounts
Registratie en login lezen/schrijven klantprofielen onder `users` in Realtime Database. In deze speeldemo wordt het wachtwoord als gewone tekst opgeslagen.

## LET OP
Dit is bewust een onbeveiligde demo. `database.rules.json` en `storage.rules` staan volledig open. Iedereen kan gegevens lezen, wijzigen en verwijderen. Beheerdersgegevens staan in openbare JavaScript en zijn zichtbaar voor bezoekers. Gebruik geen echte klantgegevens of echte wachtwoorden en zet dit niet live als echte webshop.

## Installatie
1. Controleer de Firebase-configuratie in `firebase.js`.
2. Publiceer `database.rules.json` bij Firebase Realtime Database.
3. Publiceer `storage.rules` bij Firebase Storage als je productafbeeldingen wilt uploaden.
