## Strings samenvoegen
Je kan strings en variabelen samenvoegen tot een nieuwe string op verschillende manieren:
* +-operator 
* $ string interpolation 
* Of de oude manier:  ``String.Format()`` 

{% hint style='tip' %}
In dit boek prefereren we **manier 2**, de string interpolatie. Dit is de meest moderne aanpak.
{% endhint %}

In de volgende sectie gaan we van volgende informatie uit:

* Stel dat je 2 variabelen hebt ``int age=13`` en ``string name="Finkelstein"``.
* We willen de inhoud van deze variabelen samenvoegen in een nieuwe ``string result`` die zal bestaan uit de tekst: ``Ik ben Finkelstein en ik ben 13 jaar oud.``

Volgende 3 manieren tonen hoe je steeds tot voorgaande string zal komen.

### Manier 1: String samenvoegen met de +-operator
Je kan string en variabelen eenvoudig bij elkaar 'optellen'. Ze worden dan achter elkaar geplakt als het ware. 

```csharp
string result= "Ik ben "+ name + " en ik ben "+ age+ " jaar oud.";
```

Let er op dat je tussen de aanhalingsteken (binnen de strings) spaties zet indien je het volgende deel niet tegen het vorige stringstuk wilt 'plakken'.

{% hint style='tip' %}
De volgorde van strings met andere types samenvoegen (**concateneren**) bepaalt wat de uitvoer zal zijn! Kijk zelf:

```csharp
Console.WriteLine("1"+1+1);
Console.WriteLine(1+1+"1");
Console.WriteLine("1" + (1 + 1));
```

Geef als uitvoer:

<!---{line-numbers:false}--->
```text
111
21
12
```

Ook in dit soort code wordt dus de volgorde van bewerkingen gerespecteerd. De concatenatie gebeurt van links naar rechts en de linkse operand zal steeds bepalen wat het resultaat van de bewerking zal zijn. 
{% endhint %}


### Manier 2: String interpolation met $
In de oude dagen van C# gebruikten we ``String.Format()`` (zie hierna) om meerdere strings en variabelen samen te voegen tot één string. Nu kan dat met string interpolation waarbij we het $-teken gebruiken.

Door het $-teken **VOOR** de string te plaatsen geef je aan dat alle delen in de string die tussen accolades staan { } als code mogen beschouwd worden. Een voorbeeld maakt dit duidelijk:
```csharp
string result= $"Ik ben {name} en ik ben {age} jaar oud.";
```
In dit geval zal dus de inhoud van de variabele ``name`` tussen de string op de plek waar nu ``{name}`` staat geplaatst worden. Idem voor ``age``.
Zoals je kan zien is dit veel meer leesbare code dan de eerste manier.

#### Berekeningen doen bij string interpolatie
Je mag eender welke *expressie* tussen de accolades zetten bij string interpolation, denk maar aan:
```csharp
string result= $"Ik ben {name} en ik ben {age+4} jaar oud.";
```

Alle expressies tussen de accolades zullen eerst uitgevoerd worden voor ze tussen de string worden geplaatst. De uitvoer wordt nu dus:  ```Ik ben Finkelstein en ik ben 17 jaar oud.```

Eender welke expressie is toegelaten, dus je kan ook complexe berekeningen of zelfs andere methoden aanroepen:
```csharp
string result= $"Ik ben {age*age+(3%2)} jaar oud.";
```

#### Mooier formatteren
Zowel bij manier string interpolation (manier 2) als de manier hierna kan je ook bepalen hoe de te tonen variabelen en expressies juist weergegeven moeten worden. Je geeft dit aan door na de expressie, binnen de accolades, een dubbelpunt te plaatsen gevolgd door de manier waarop moet geformatteerd worden:

Wil je bijvoorbeeld een kommagetal tonen met maar 2 cijfers na de komma dan schrijf je:

```csharp
double number = 12.345;
Console.WriteLine($"{number:F2}");
```

{% hint style='tip' %}
Nog enkele nuttige vormen:
* D5: geheel getal bestaande uit 5 cijfers (``123`` wordt ``00123``) (werkt enkel op gehele getallen!)
* E2: wetenschappelijke notatie met 2 cijfers precisie (``12000000`` wordt ``1,20E+007``)
* C: geldbedrag (``12,34`` wordt € 12,34: teken van valuta afhankelijk van instellingen pc)

  
Alle format specifiers staan [hier opgelijst](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings).
{% endhint %}

### Manier 3: String.Format()
String interpolatie met het $-teken is een nieuwe C# aanwinst. Je zal echter nog veel documentatie en online code tegenkomen die nog met ``String.Format`` werkt (ook zijn er nog zaken waar het te prefereren is om ``String.Format`` te gebruiken i.p.v. 1 van vorige manieren). Om die reden bespreken we dit nog in dit boek.

``String.Format`` is een ingebouwde methode die string-interpolatie toelaat op een iets minder intuïtieve manier:
```csharp
string result= String.Format("Ik ben {0} en ik ben {1} jaar oud.",name,age);
```
Het getal tussen de accolades geeft aan de hoeveelste parameter na de string hier in de plaats moet gezet worden (0= de eerste, 1= de tweede, enz).

Volgende code zal een ander resultaat geven:
```csharp
string result= String.Format("Ik ben {1} en ben {1} jaar.",name,age);
```
Namelijk:  ``Ik ben 13 en ik ben 13 jaar oud.``

<!---NOBOOKSTART--->
### Kennisclip
![](../assets/infoclip.png)

* [String interpolation](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=a3d572bc-f72d-4622-9875-abe300b9ecf7)
<!---NOBOOKEND--->