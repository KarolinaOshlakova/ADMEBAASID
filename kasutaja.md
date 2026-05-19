## SQL SERVER - kasutajate autentimine ja õiguste haödamine

**SQL serveris kasutatakse kahte peamist autentimise tüüpi:**

1. Windows Authentication Selle puhul kasutatkse samu kasutajaandemid,millega logitakse sisse Windows operatsioonisüsteemi
>Kasutajanimi ja parool on seotud windowsiga.Turvalisem lahendus. Paroole haldab Windows. Kasutaja ei pea eraldi SQL Serveri parooli teadma.

2. SQL Server Authentication
>Selle puhul luuakse kasutaja otse SQL Serverisse. Kasutaja ei ole seotud Windowsiga. Määratakse eraldi kasutajanimi ja parool. Sobib veebirakenduste jaoks.

## Näide kasutajast: Directorlrina. Parool: director

**Kasutaja loomine SQL Serveris**






