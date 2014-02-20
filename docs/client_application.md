##Introduktion till uppgiften - Klientapplikation via AngularJS##
I förra uppgiften skapade vi ett restful-inspirerat webb-API som nu förhoppningsvis är redo för användning. Det är nu du ska använda ditt API för att att skapa en webbaserad klientapplikation som genom asynkrona anrop jobbar mot ditt API.

Uppgiften kan innebära vissa förändingar i ditt API och dess datamodell och ditt tidigare utvecklade API.


## Hantering av användare ##
En av fördelarna med att bygga ett RESTful API är att vi har ett oberoende mellan serv- och klientapplikation. Vi skulle kunna använda den lösning vi implementerade i API-uppgiften för att ha kvar detta men vi kommer delvis bryta det oberoendet genom att nu låta användaren av klientapplikationen logga in via githubs OAuth-lösning och därmed låta github ta hand om själva autensieringen av användarna och använda detta i vårt API. Därför får vi se detta mer som en övning för ert lärande än som en skarp implementation.

Detta kommer förmodligen innebära vissa förändringar i din datamodell till din användarhantering vilket tack och lov underlättas av migreringsmöjligheten som finns i Ruby On Rails. Github har en möjlighet att logga in användare via en 3-legged OAuth2.0. Detta ger oss möjlighet att på serversidan (webb-API:et) få reda på användaruppgifter från github och använda dessa i ditt API och autentisera och aktorisera användarna av ditt API.

Du kan via github (och användarens tillstånd) läsa ut ett användarid (github-id) samt användaruppgifter för att lagra dessa i din User-modell. Var dock noga med att inte spara dubbletter av användare samt att en användare kan ändra vissa uppgifter på sitt github-konto som då också bör ändras i din lagring (github-ID borde dock alltid vara konstant). Då OAuth-inloggningen lyckats kan vi generera en access_token för våra API-klienter
Jag kan rekommendera att undersöka gem:et [OmniAuth](https://github.com/intridea/omniauth) samt denna [railscast](http://railscasts.com/episodes/241-simple-omniauth) för att göra din implementation kring detta.

##Krav på applikationen##

* Inloggningen av användare (resursägare) ska ske via github via deras OAuth-inloggning. (Se punkt nedan)
* Klientapplikationen ska vara skriven i angularJS och använda asynkrona anrop mot ditt tidigare skrivna API. Anropen mot githubs OAuth-provider behöver ej vara asynkront.
* Applikationen ska kunna bistå sin användare med följande:
	* Möjlighet att logga in med sina github-uppgifter
	* Möjlighet att på ett genomtänkt och överskådligt sätt lista tjänstens alla resurser (tänk på att det kan finnas obegränsat antal - Vi kan inte visa alla på en gång)
	* Möjlighet att kunna söka specifika resurser i tjänsten genom sökord
	* Möjlighet att kunna filtrera ut resurser beroende på vald tagg, resurstyp, licens och användare
* Användaren ska hela tiden veta vad som pågår i applikationen med hjälp av tydliga meddelanden och uppdatering av gränssnitt
* Webbapplikationen ska ha en genomarbetad design och vara responsiv. Ett css-ramverk så som bootstrap eller foundation ska användas.
* Gränssnittet ska vara utformat på sådant sätt att man intuitivt förstår hur applikationen fungerar. 
* Applikationen ska bete sig som en Single Page Application
* Webbläsarens bakåt- och framåtknappar ska fungera som på en "vanlig" webbsida
* Koden ska publiceras på github på ditt repositorie som är kopplat till kursen

## Extra funktioner som kan anses betygshöjande ##

* Skriv din applikation med tillhörande testfall i AngularJS
* Implementera en cache-strategi
* Designmässigt ögongodis så som animationer
* Ytterligare applikationsmässiga funktioner som höjer upplevelsen
