## Methoden met arrays als parameter maken

Zoals alle datatypes kan je ook arrays van eender welk datatype als parameter gebruiken bij het schrijven van een methode.

{% hint style='warning' %}
**Opgelet:**
Herinner je dat arrays *by reference* werken. Je werkt dus steeds met de eigenlijke array, ook in de methode. Als je dus aanpassingen aan de array aanbrengt in de methode, dan zal dit ook gevolgen hebben op de array van de parent-methode (logisch: het gaat om dezelfde array).
{% endhint %}

Stel dat je bijvoorbeeld een methode hebt die als parameter 1 array van ints meekrijgt. De methode zou er dan als volgt uitzien.

```csharp
static void EenVoorbeeldMethode(int[] inArray)
{
 
}
```

Om deze methode aan te roepen volstaat het om een bestaande arrays nu als parameter mee te geven:

```csharp
int[] getallen = {1, 2, 3};
EenVoorbeeldMethode(getallen);
```

### Array grootte in de methode
Een array als parameter meegeven kan dus, maar een ander aspect waar rekening mee gehouden moet worden is dat je niet kan ingeven in de parameterlijst hoe groot de array is. Je zal dus in je methode steeds de grootte van de array moeten uitlezen met de ``.Length``-eigenschap.

Volgende methodesignatuur is dus **FOUT**!

```csharp 
static void EenVoorbeeldMethode(ref int[6] inArray)
{
 
}
```
En zal volgende error genereren:

!["Array size cannot be specified in a variable declaration." Duidelijk toch!](../assets/5_arrays/arrays3.png)

### Arraymethode voorbeeld

Volgend voorbeeld toont een methode die alle getallen van de array op het scherm zal tonen:

```csharp
static void ToonArray(int[] getalArray)
{
    Console.WriteLine("Array output:");
    for (int i = 0; i < getalArray.Length; i++)
    {
        Console.WriteLine(getalArray[i]);
    }
}
```


De ``ToonArray`` methode aanroepen kan dan als volgt:

```csharp
int[] leeftijden = {2, 5, 1, 6};
ToonArray(leeftijden);
``` 
En de output zal dan zijn:

<!---{line-numbers:false}--->
```
Array output:
2
5
1
6
```

### Voorbeeldprogramma met methoden
Volgend programma toont hoe we verschillende onderdelen van de code in methoden hebben geplaatst zodat:

1. de lezer van de code sneller kan zien wat het programma juist doet
2. zodat code herbruikbaar is


```csharp
static void VulArray(int[] getalArray)
{
    for (int i = 0; i < getalArray.Length; i++)
    {
        getalArray[i] = i;
    }
}

static void VermenigvuldigArray(int[] getalArray, int multiplier)
{
    for (int i = 0; i < getalArray.Length; i++)
    {
        getalArray[i] = getalArray[i] * multiplier;
    }
}

static void ToonVeelvouden(int[] getalArray, int veelvoudenvan)
{
    for (int i = 0; i < getalArray.Length; i++)
    {
        if (getalArray[i] % veelvoudenvan == 0)
            Console.WriteLine(getalArray[i]);
    }
}

static void Main(string[] args)
{
    int[] getallen = new int[100];
    VulArray(getallen);
    //Alle elementen met 3 vermenigvuldigen
    VermenigvuldigArray(getallen, 3);
    //Enkel veelvouden van 4 op het scherm tonen
    ToonVeelvouden(getallen, 4);
} 
```

### Array als return-type bij een methode

Ook methoden kun je natuurlijk een array als returntype laten geven. Hiervoor zet je gewoon het type array als returntype (wederom zonder de grootte) in de methode-signature.

Stel bijvoorbeeld dat je een methode hebt die een int-array aanmaakt van een gegeven grootte waarbij ieder element van de array reeds een beginwaarde heeft die je ook als parameter meegeeft:

```csharp
static int[] MaakArray(int lengte, int beginwaarde)
{
    int[] resultArray = new int[lengte];
    for (int i = 0; i < lengte; i++)
    {
        resultArray[i] = beginwaarde;
    }
    return resultArray;
}
```
De aanroep van deze methode vereist dan dat je het resultaat opvangt in een nieuwe variabele, als volgt:

```csharp
int[] mijnNieuweArray= MaakArray(4,666);
```

{% hint style='warning' %}
Onthoud dat arrays altijd **by reference** naar en van methoden komen. Je werkt dus op de originele array, niet op een kopie er van!
{% endhint %}