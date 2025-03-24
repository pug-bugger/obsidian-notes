inbound wrapper have DTO mock.
atsirado outbound wrapperis.

link to doc: [Code Review Guideline](https://docs.google.com/document/d/1VMZQANN56XOgVFjBbz3OSrnD3MoyYkMQDHDoq-j9N8I/edit?tab=t.0#heading=h.6945m9hdu5bq)

**selectById**
turi buti kuo universalesne, bet kai matosi kad metdo perpanaudojamumo kodo coverage yra mazas.

Kurioj vietoj tikrinti input parametrus?
Service layer logika atsako uz input parametru likrinima, selektor turi grazinti tuscia lista jeigu parametru nera.

TODO komentarus galima rasyti

**ServiceLayer**
Service gali kviesti kita service, bet dazniausiai be naujo uow konteksto, o jeigu reikia, perduoti kaip paraetra.
Jeigu matosi kad domai kvieciasi vienam domai'ui, tai galbut for loop galim deti i domain.

**DomainLayer** duomenu manipulacijom
Service daugiau duomenu apdorojimus daryti o domaine labiau apdorotus perduoti.
