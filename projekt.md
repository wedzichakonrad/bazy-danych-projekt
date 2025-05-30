### produkty

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_produktu** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_produkty_id_produktu_szczegóły_transakcji | |
| **nazwa** | VARCHAR(40) | not null |  | |
| **cena_sztuki** | FLOAT | not null |  | |
| **kategoria** | VARCHAR(40) | not null |  | |
| **na_recepte** | BOOLEAN | not null |  | |
| **producent** | VARCHAR(40) | not null |  | |
| **stan** | INTEGER | not null |  | |
| **id_promocji** | INTEGER | not null | fk_produkty_id_promocji_promocje | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| table_0_index_0 |  |  |
### transakcje

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_transakcji** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_transakcje_id_transakcji_szczegóły_transakcji | |
| **data** | DATE | not null |  | |
| **id_pracownika** | INTEGER | not null |  | |
| **id_klienta** | INTEGER | not null |  | |
| **cena** | FLOAT | not null |  | | 


### szczegóły_transakcji

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_transakcji** | INTEGER | 🔑 PK, not null, unique, autoincrement |  | |
| **id_produktu** | INTEGER | 🔑 PK, not null |  | |
| **ilość** | INTEGER | not null |  | | 


### szczegóły_recepty

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_recepty** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_szczegóły_recepty_id_recepty_recepty | |
| **id_produktu** | INTEGER | 🔑 PK, not null |  | |
| **ilość** | INTEGER | not null |  | | 


### recepty

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_recepty** | INTEGER | 🔑 PK, not null, unique, autoincrement |  | |
| **id_klienta** | INTEGER | not null |  | |
| **data_wystawienia** | DATE | not null |  | |
| **id_doktora** | INTEGER | not null |  | | 


### doktorzy

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_doktora** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_doktorzy_id_doktora_recepty | |
| **imię** | VARCHAR(40) | not null |  | |
| **nazwisko** | VARCHAR(40) | not null |  | |
| **specjalizacja** | VARCHAR(40) | not null |  | | 


### dostawcy

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_dostawcy** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_dostawcy_id_dostawcy_dostawy_produktów | |
| **nazwa** | VARCHAR(40) | not null |  | |
| **kraj** | VARCHAR(40) | not null |  | |
| **miasto** | VARCHAR(40) | not null |  | |
| **ulica** | VARCHAR(40) | not null |  | |
| **kod_pocztowy** | VARCHAR(20) | not null |  | |
| **strona_internetowa** | VARCHAR(40) | not null |  | | 


### dostawy_produktów

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_dostawy** | INTEGER | 🔑 PK, not null, unique, autoincrement |  | |
| **id_dostawcy** | INTEGER | 🔑 PK, not null |  | |
| **data_dostawy** | DATE | not null |  | | 


### szczegóły_dostawy

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_dostawy** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_szczegóły_dostawy_id_dostawy_dostawy_produktów | |
| **id_partii** | INTEGER | 🔑 PK, not null |  | |
| **cena_dostawy** | FLOAT | not null |  | | 


### partie

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_partii** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_partie_id_partii_szczegóły_dostawy | |
| **id_produktu** | INTEGER | not null | fk_partie_id_produktu_produkty | |
| **data_ważności** | DATE | not null |  | |
| **ilość** | INTEGER | not null |  | | 


### pracownicy

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_pracownika** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_pracownicy_id_pracownika_transakcje | |
| **imię** | VARCHAR(40) | not null |  | |
| **nazwisko** | VARCHAR(40) | not null |  | |
| **stanowisko** | VARCHAR(40) | not null |  | |
| **nr_komórkowy** | INTEGER | not null |  | |
| **email** | VARCHAR(40) | not null |  | | 


### reklamacje

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_reklamacji** | INTEGER | 🔑 PK, not null, unique, autoincrement |  | |
| **data_reklamacji** | DATE | not null |  | |
| **id_transakcji** | INTEGER | not null | fk_reklamacje_id_transakcji_transakcje | | 


### klienci

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_klienta** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_klienci_id_klienta_recepty,fk_klienci_id_klienta_transakcje | |
| **imię** | VARCHAR(40) | not null |  | |
| **nazwisko** | VARCHAR(40) | not null |  | |
| **pesel** | INTEGER | not null |  | | 


### promocje

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_promocji** | INTEGER | 🔑 PK, not null, unique, autoincrement | fk_promocje_id_promocji_szczegóły_promocji | |
| **data_wygaśnięcia** | DATE | not null |  | | 


### szczegóły_promocji

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_promocji** | INTEGER | 🔑 PK, not null, unique, autoincrement |  | |
| **id_produktu** | INTEGER | 🔑 PK, not null |  | |
| **wysokość_promocji** | FLOAT | not null |  | | 

