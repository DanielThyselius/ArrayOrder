# Övning: Orderhanteringssystem med arrayer
## Scenario
Ni arbetar med att bygga ett orderhanteringssystem för en webbutik. På grund av begränsningar i systemet får ni inte använda några inbyggda samlingsklasser som `List<T>` eller funktioner i `Array` för sökning och sortering. Istället måste ni använda arrayer för att hantera produkter och order. Detta innebär att ni måste implementera egna algoritmer för att:

- Söka och filtrera produkter.
- Sortera produkter.
- Dynamiskt hantera storleken på arrayer.

### Viktiga begränsningar 
> Ni får **inte** använda några inbyggda samlingsklasser eller funktioner för sökning, sortering eller filtrering.
>
> **Vad innebär detta?**
> - Ni får **inte** använda `List<T>`, `Dictionary<TKey, TValue>` eller andra samlingsklasser. Alla data ska hanteras med arrayer.
> - Ni får **inte** använda inbyggda funktioner som:
>   - `Array.Sort` – för sortering.
>   - `Array.Find` eller `Array.FindIndex` – för sökning.
>   - `Array.BinarySearch` – för effektiv sökning.
>   - LINQ-metoder som `Where`, `OrderBy`, `Select`, etc.

## Kravspecifikation

### 1. Lagersaldo
#### Skapa en metod som heter `UpdateStock` i klassen `Product`. Den ska:

*   Ta två parametrar:
    *   `int amount` – Antalet produkter som ska läggas till eller tas bort från lagret.
    *   `bool isDelivery` – Om `true` är det en leverans till lagret (öka lagret), annars är det en försäljning (minska lagret).
*   Uppdatera lagersaldot (`ILager`) för produkten baserat på dessa parametrar.
*   Validera indata och hantera följande situationer:
    *   Om `amount` är 0 eller negativt, kasta en `ArgumentException` med ett tydligt felmeddelande.
    *   Om `isDelivery` är `false` (försäljning) och `amount` är större än lagersaldot, kasta en `InvalidOperationException`.
    *   Om `isDelivery` är `true` och `amount` överstiger 10 000 (valfri gräns för stora leveranser), kasta en `InvalidOperationException` (valfritt för att skapa fler testfall).

#### Tester för `UpdateStock`
Eftersom metoden har flera möjliga utfall beroende på indata, behöver vi skriva flera tester för att täcka alla scenarier.

##### Testfall för leveranser (`isDelivery = true`):
*   Vanlig leverans (öka lagret).
*   Leverans med ogiltig mängd (0 eller negativt värde).
*   Leverans som överstiger gränsen (valfritt krav).

##### Testfall för försäljning (`isDelivery = false`):
*   Vanlig försäljning (minska lagret).
*   Försäljning med ogiltig mängd (0 eller negativt värde).
*   Försäljning som överskrider lagersaldot.

### 2. Produkthantering
Produkterna ska lagras i en array. Ni ska implementera följande funktioner:

- Lägga till en produkt i arrayen (hantera om arrayen blir full genom att skapa en ny, större array).
- Ta bort en produkt från arrayen baserat på dess Id.
- Söka efter en produkt baserat på namn eller kategori (implementera en linjär sökalgoritm).


### 3. Sortering av produkter
Implementera egna algoritmer för att sortera arrayen med produkter:

- Sortering efter pris (stigande och fallande).
- Sortering efter namn (alfabetisk ordning).
- Sortering efter kategori.

### 4. Filtrering av produkter
Implementera en filtreringsfunktion som returnerar en ny array med produkter baserat på:

- Prisintervall.
- Lagerstatus (om produkter finns i lager).
- Kategori.
