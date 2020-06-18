# Teknisk informasjon

## Hvor kommer trafikken fra?

All trafikk fra Allvis NOR sendes fra adresser i området
`91.206.34.208/28`.

Portskanning skjer fra disse adressene:

* `91.206.34.210` (scan01.allvis.no)
* `91.206.34.211` (scan02.allvis.no)

Automatiserte undersøkelser av åpne porter kommer fra disse adressene:

* `91.206.34.212` (probe01.allvis.no)
* `91.206.34.213` (probe02.allvis.no)

Trafikk vil også komme fra andre adresser i det nevnte /28-nettet, for
eksempel ved manuelle undersøkelser eller som følge av interne
endringer. Eventuell hvitelisting av adresser bør dekke hele dette
nettet.

!> Det er generelt ikke ønskelig at trafikk fra Allvis NOR slippes
   ukritisk gjennom utvendig brannmur. Vi ønsker at angrepsflaten
   observert av Allvis NOR skal være den samme som for andre aktører
   på Internett, og vi mener at dette også gir mest verdi for
   virksomheten. Dette omfatter dog *ikke* TCP-akseleratorer som
   implementerer SYN cookies, hvor vi faktisk ønsker at det [legges
   inn unntak](#tcp-akseleratorer).

Enkelte ganger kan det også komme trafikk fra andre adresser i NSMs
adresseområde (`91.206.34.0/24`).

## Trafikkvolum

Vi skanner for tiden alle TCP-porter fra 1 til 65535. Internt i
systemet knyttes ett eller flere adresseområder til en gruppe, og hver
gruppe tilordnes en bestemt pakkerate basert på totalt antall adresser
og ønsket kartleggingsintervall.

Vanligvis tilstreber vi å dekke alle TCP-porter i en gruppe over en
periode på 14 dager. For et /24-nett med 256 adresser betyr dette at
pakkeraten vil være ca. 14 pps. Mindre nett og enkeltadresser tildeles
gjerne en kortere periode enn 14 dager. Følgende tabell viser typiske
pakkerater for nett av ulike størrelser.

| Størrelse   | Pakkerate |
| ----------- | --------: |
| /32 (1)     |   0.2 pps |
| /27 (32)    |     2 pps |
| /24 (256)   |    14 pps |
| /18 (16384) |   888 pps |
| /17 (32768) |  1000 pps |
| /16 (65536) |  1000 pps |

Vi har imidlertid satt en intern begrensning på 1000 pps per
gruppe. Dette betyr i praksis at /17-nett og større (for eksempel /16
og /15) vil ta tilsvarende lenger tid å kartlegge. Et /16-nett
kartlegges typisk over en periode på 50 dager. /15-nett legges gjerne
inn som to /16-nett, noe som gir 2000 pps totalt.

## TCP-akseleratorer

?> Kortversjon: legg inn unntak for IP-adressene våre i eventuelle
   beskyttelsesmekanismer som SYN-cookies eller (D)DoS-beskyttelse.

Fra tid til annen ser vi bruk av
[SYN cookies](https://en.wikipedia.org/wiki/SYN_cookies) på brannmurer
eller lignende enheter. Dette innebærer typisk at enheten sender
SYN/ACK-svar på alle SYN-pakker som sendes av portskanneren vår.
Denne mekanismen slår gjerne inn først når samlet volum av SYN-pakker
gjennom enheten overstiger en viss terskel, og er ment å beskytte
maskinen eller tjenesten som ligger bak mot overbelastning.

Dessverre er det vanskelig for oss å skille mellom «reelle»
SYN/ACK-pakker og SYN/ACK-pakker som genereres av en brannmur. I beste
fall vil slik oppførsel gi falske positive i listen over åpne
porter. I verste fall går det utover ytelsen til systemene våre.

Hvis mulig ønsker vi at det legges inn et unntak for IP-adressene våre
i enheter som har SYN cookies aktivert. De fleste brannmurer har
støtte for slike unntak.
