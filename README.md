# Webshop

A következő feladatban egy sportklub szurkolói webshopjának adataival kell dolgoznia. Az adatbázisban a 2018. januári értékesítési adatok találhatók. Az adatbázis a következő táblákat tartalmazza (félkövér betűvel a tábla neve, alatta a mezőnevek):

|  termekek  |         (id, megnevezes, ar)         |
|:----------:|:------------------------------------:|
|     id     |    Egész szám, a termék kódja, *PK*    |
| megnevezes |         Szöveg, a termék neve        |
|     ar     | Numerikus, a termék bruttó egységára |

|     vevok    |     (id, nev, iranyitoszam, telepules, utcahazszam)    |
|:------------:|:------------------------------------------------------:|
|      id      |           Egész szám, a vevő azonosítója, *PK*           |
|      nev     |                   Szöveg, a vevő neve                  |
| iranyitoszam |    Szöveg, a vevő szállítási címéből az irányítószám   |
|   telepules  |   Szöveg, a vevő szállítási címéből a település neve   |
|  utcahazszam | Szöveg, a vevő szállítási címéből az utca és a házszám |

|  szamlafej |           (id, szamlaszam, kelt, teljesites, vevoid)           |
|:----------:|:--------------------------------------------------------------:|
|     id     |              Egész szám, a számla azonosítója, *PK*              |
| szamlaszam |            Szöveg, a kiállított számla száma, egyedi           |
|    kelt    |               Dátum, a számla kiállításának kelte              |
| teljesites | Dátum, a számla teljesítésének, azaz a kiszállításnak a dátuma |
|   vevoid   |          Egész szám, a vevő kódja a vevok táblából, *FK*         |


 
|    szamlatetel   | (id, szamlafejid, termekid, mennyiseg, mennyisegieg, bruttoegysegar, afaszazalek) |
|:----------------:|:---------------------------------------------------------------------------------------------------:|
|        id        |                              Egész szám, a számlatétel azonosítója, PK                              |
|    szamlafejid   |                      Egész szám, a számla azonosítója a szamlafej táblából, *FK*                      |
|     termekid     |                       Egész szám, a termék azonosítója a termekek táblából, *FK*                      |
|     mennyiseg    |                              Egész szám, a termékből rendelt mennyiség                              |
| mennyisegiegyseg |                  Szöveg, a termék mennyiségi egysége (minden rekord esetében „db")                  |
|  bruttoegysegar  |                         Numerikus, 1 db termék bruttó egységára az eladáskor                        |
|    afaszazalek   |         Egész szám, az eladáskor a termékre érvényes áfaszázalék (minden rekord esetében 27)        |
 
 
Az elsődleges kulcsokat *PK*-val, az idegenkulcsokat *FK*-val jelöltük. A mező neve után annak típusa és leírása található. A feladatok pontosabb megértéséhez tanulmányozza a táblákban lévő rekordokat is!

A feladatok megoldására elkészített SQL parancsokat a **megoldasok.sql** állományba illessze be a feladatok végén zárójelben jelölt sor alá! A javítás során csak ennek az állománynak a tartalma kerül értékelésre.
Ügyeljen arra, hogy a lekérdezésben pontosan a kívánt mezők a megadott névvel szerepeljenek, és felesleges mezőt ne jelenítsen meg!

1. Hozzon létre a lokális SQL szerveren webshop néven adatbázist! Az adatbázis alapértelmezett rendezési sorrendje a magyar szabályok szerinti legyen! Ha az Ön által választott SQL szervernél nem alapértelmezés az **UTF-8** kódolás, akkor azt is állítsa be alapértelmezettnek az adatbázis létrehozásánál! (1. feladat:) 

2. A **tablak.sql** és az **adatok.sql** állományok tartalmazzák a táblákat létrehozó és az adatokat a táblába beszúró SQL parancsokat! Futtassa elsőként a **tablak.sql**, majd az **adatok.sql** parancsfájlt a webshop adatbázisban!

3. Állítsa be a következő ábra szerint és a fenti leírás alapján az idegenkulcsokat a szamlafej és a szamlatetel táblákban! (3. feladat:) 

    ![](https://i.imgur.com/vMm0YqQ.jpg)


4.	Készítsen lekérdezést a webshop által kínált termékekről! A listában szerepeljen a termék neve és jelenlegi bruttó ára! A listát a termékek ára szerint növekvő sorrendbe rendezze! (4. feladat:)


    ```TXT
    Sörnyitó    |   600
    Kulacs      |   1200
    Hűtőmágnes  |   1500
    Kulcstartó  |   1500
    ```

5.	A bolt vezetése úgy döntött, hogy minden 5 000 Ft-nál drágább termék árát csökkenti 5%-kal. Végezze el az árak aktualizálását a termékek táblán (5. feladat:)!


    ```TXT
    9 sor érintett. (A lekérdezés 0.0060 másodpercig tartott.)
    ```

6.	Lekérdezéssel határozza meg, mekkora volt a bruttó árbevétele a boltnak **2018.01.01** és **2018.01.15** között! A dátum ellenőrzésekor a számla teljesítési dátumát vegye alapul! Ügyeljen arra, hogy a számlatételben a bruttó egységár csak 1 db termékre vonatkozik! (6. feladat:)


    ```TXT
    2691200
    ```

7.	Listázza ki azokat a vevőket (név, település neve), akik szerepelnek a bolt nyilvántartásában, de januárban nem vásároltak! A listát névsorban jelenítse meg! (7. feladat:)


    ```TXT
    Antal Andrea    |   Debrecen
    Balázs Andrea   |   Siófok
    Bíró Mária      |   Pápa
    Fehér Sándor    |   Pécs
    ```

8.	Listázza ki, hogy az árbevétel alapján melyik volt a három legnépszerűbb termék a vizsgált januári időszakban! A listában szerepeljen a termék neve és a bruttó árbevétel összege, árbevétel szerint csökkenő sorrendben! (8. feladat:)


    ```TXT
    Hivatalos mez       |   1194000
    Szabadidő felső     |   652500
    Vásárlási utalvány  |   580000
    ```




