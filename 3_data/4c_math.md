## Berekeningen met System.Math

Een groot deel van je leven als ontwikkelaar zal bestaan uit het bewerken van variabelen in code. Meestal zullen die bewerkingen voorafgaan van berekeningen. De ``System.Math`` bibliotheek zal ons hier bij kunnen helpen.


### De Math bibliotheek
De Math bibliotheek bevat aardig wat handige methoden. Deze bibliotheek bevat methoden voor een groot aantal typische wiskundige methoden (sinus, cosinus, vierkantswortel, macht, afronden, etc.) en kan je dus helpen om leesbaardere expressies te schrijven.

Stel dat je de derde macht van een variabel ``getal`` wenst te berekenen. *zonder* de Math-bibliotheek zou dat er zou uitzien:
```csharp
double result= getal * getal * getal;  //SLECHTE MANIER
```
Dit valt nog mee, maar wat als je 3 tot de zevende macht moest berekenen? Kortom, laten we eens kijken hoe ``Math`` ons kan helpen. 


*Met* de Math-bibliotheek kunnen we gebruik maken van de ``Pow`` (Power) methode:
```csharp
double result= Math.Pow(getal, 3);
```

Deze methode vereist twee parameters:
* De eerste is het grondtal 
* De tweede is de exponent ("tot de hoeveelste macht")

#### De Math bibliotheek ontdekken

Als je in Visual Studio ``Math`` schrijft, gevolgd door een punt (``.``) krijg je alles te zien wat de Math-bibliotheek kan doen:


![De sterretjes geven de meestgebruikte methoden in deze bibliotheek aan. Vervolgens verschijnen alle overige methoden alfabetisch.](../assets/4_methoden/methoden3.png)


{% hint style='tip' %}
Een kubusje voor een naam wil zeggen dat het om een **Methode** gaat (zoals ``Console.ReadLine()``). Een vierkantje met twee streepjes in zijn constanten (zoals ``Pi``(``π``) en het getal van Euler (``e``)).
{% endhint %}

#### Methoden gebruiken

De meeste methoden zijn zeer makkelijk in gebruik en werken op dezelfde manier. Meestal moet je 1 of meerdere parameters tussen de haken meegeven en het resultaat moet je altijd in een nieuwe variabele opvangen. 

Enkele voorbeelden:

```csharp
double sineHoekA= Math.Sin(345); //IN RADIALEN!
double DerdeMachtVan20= Math.Pow(20, 3);
double complex= 3+ DerdeMachtVan20 * Math.Round(sineHoekA);
```

Twijfel je over de werking van een methode, gebruik dan de help als volgt:

1. Schrijf de Methode zonder argumenten. Bijvoorbeeld ``Math.Pow()`` (je mag de rode error negeren). 
2. Plaats je cursor op ``Pow``.
3. Druk op ``F1`` op je toetsenbord.
4. Je krijgt nu de help-files te zien van deze methode.

#### PI (π)

Ook het getal Pi  (``3.141...``) is beschikbaar in de Math-bibliotheek. Het witte icoontje voor PI bij Intellisense toont aan dat het hier om een *field* gaat: een eenvoudige variabele met een specifieke waarde. In dit geval gaat het zelfs om een ``const`` field, met de waarde van Pi van het type double.

```csharp
public const double PI;
```

Je kan deze als volgt gebruiken in berekeningen:

```csharp
double straal= 5.5;
double omtrek= Math.PI * 2 * straal;
```

{% hint style='tip' %}
**``const``**
Je zal het ``const`` keyword hier en daar in codevoorbeelden zien staan. Je kan dit gebruiken om aan te geven dat een variabele onveranderlijk is én niet per ongeluk kan aangepast worden. Je mag dit dus ook zelf gebruiken zoals in volgende voorbeeld:

```csharp
const double gAarde= 9.81;
gAarde= 10.48; //ZAL ERROR GEVEN
```
{% endhint %}


<!---NOBOOKSTART--->
### Kennisclip
![](../assets/infoclip.png)
* [De Math-bibliotheek](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=4d790ab9-e3b9-4e4b-bf59-a976007197fa)

<!---NOBOOKEND--->