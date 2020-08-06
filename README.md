# Allvis NOR

Allvis NOR er navnet på [Nasjonal sikkerhetsmyndighets](https://nsm.no/)
automatiserte sårbarhetskartlegger. Dette er en tjeneste som tilbys
til offentlige virksomheter og eiere av kritisk infrastruktur. Den
er internt utviklet og driftes av NSM ved seksjon for
inntrengingstesting.

Her kan du finne informasjon om hvordan virksomheten din kan [komme i
gang](get-started.md) med Allvis NOR, [teknisk
informasjon](technical.md) om hvordan tjenesten fungerer, samt
informasjon om det nye [API-et](api.md) vi tilbyr til alle deltakende
virksomheter.

## Hvordan kartleggingen fungerer

Allvis NOR kartlegger først hvilke tjenester som eksponeres i
virksomhetens adresserom med en portskanner. Når det oppdages en
tjeneste kjøres en rekke automatiserte tester mot denne, blant annet
for å finne ut hvilken protokoll og programvare som brukes.

Når vi har samlet inn litt basisinformasjon om tjenesten vil vi typisk
kjøre tester som retter seg mot spesifikke protokoller eller
programvarer, og det er i denne fasen de fleste automatiserte
sårbarhetsjekkene gjøres.

Hvis det oppdages en sårbarhet vil denne flagges i våre interne
systemer, slik at vi kan sende ut et varsel. I noen tilfeller
verifiserer vi sårbarheten manuelt før varsel sendes ut.

## Hvorfor Allvis NOR?

Allvis NOR er et lavterskeltilbud som skal kreve lite innsats men
samtidig gi stor verdi. Fordi tjenesten for tiden tilbys
vederlagsfritt og risikoen ved å delta [er lav](get-started.md#risiko),
mener vi at det er liten grunn til å ikke la seg kartlegge.

Hvis virksomheten deres allerede bruker et lignende produkt kan det
fortsatt være gunstig å supplere med Allvis NOR. Vi håper og tror at
vi kan skille oss litt fra lignende produkter på flere måter.

* Grundig kartlegging: vi dekker og samler inn informasjon fra alle
  TCP-porter, ikke bare et begrenset utvalg.
* Manuell analyse av resultater: vi prøver å kaste et menneskelig
  blikk på de fleste tjenester som oppdages, og bruker blant annet
  erfaringer fra inntrengingstesting til å vurdere om en tjeneste kan
  være sårbar.
* Responsevne ved hendelser: når informasjon om nye sårbarheter gjøres
  kjent eller det inntreffer andre sikkerhetsrelevante hendelser så
  sitter vi på en god oversikt over eksponerte tjenester hos den
  enkelte virksomhet, og kan raskt gjøre oppslag og undersøkelser i
  dette datagrunnlaget.

Ved å bruke [API-et](api.md) kan det også være mulig å importere
resultater fra Allvis NOR i andre verktøy.

?> Vil du vite mer? Fortsett ved å lese om hvordan dere kan [komme i
    gang](get-started.md) med Allvis NOR.
