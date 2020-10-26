# Klassen und Instanzen

## Wiederholung: 

* Eine Klasse wird mit Schlüsselwort `class` geschrieben. 
    * **Tipp:** nach guter Praxis: Klassennamen beginnen mit einem großen Buchstaben.
* Eine Klasse hat normalerweise eine Methode `constructor()`, um ihren Startzustand zu setzen.
* Eine Klasse kann Methoden haben. Diese können innere Eigenschaften mit dem  `this` Schlüsselwort aufrufen (this ist die Referenz auf die Instanz, die erstellt wurde).

    Beispiel (Definition):
    ```javascript
    class MeineKlasse {
        constructor(startWert1, startWert2) {
            this.Eigenschaft1 = startWert1;
            this.Eigenschaft2 = startWert2;
        }

        eineMethode() {
            console.log("Eigenschaft1: ",this.Eigenschaft1);
            console.log("Eigenschaft2: ",this.Eigenschaft2);
        }
    }
    ```

* Um eine Instanz einer Klasse zu erstellen (ein Objekt), benutze das `new` Schlüsselwort mit dem Namen der Klasse und runden Klammern ().
    * Das ruft die Methode `constructor()` auf und erwartet, dass Argumente für den Startzustand übergeben werden.
* Normalerweise, können Eigenschaften gelesen und geschrieben werden. Dazu schreiben wir die Instanz gefolgt von einem Punkt(.) und dem Namen der Eigenschaft.
* Um eine Methode einer Klasse aufzurufen, verwende den Namen der Instanz gefolgt von einem Punkt (.) und dem Methodennamen mit runden Klammern(), die Argumente für die Methode enthält (falls an der Methode Parameter definiert wurden).

    Beispiel (benutzen):
    ```javascript
    let meineInstanz = new MeineKlasse("Inhalt erste Eigenschaft",100);
    myInstance.Eigenschaft1 = "Inhalt 1. Eigenschaft";
    myInstance.eineMethode();
    /* erwartete Ausgabe:
    Eigenschaft1: Inhalt 1. Eigenschaft
    Eigenschaft2: 100
    */
    ```
* Du kannst prüfen, ob ein Objekt aus einer Klasse als Vorlage erstellt wurde, mit dem operator `instanceof`.

    Beispiel:
    ```javascript
    let eineInstanz = new MeineKlasse("erster", "zweiter");
    let keineInstanz = {Eigenschaft1: "foo", Eigenschaft2: "bar"};
    console.log(eineInstanz instanceof MeineKlasse);
    // -> true
    console.log(keineInstanz instanceof MeineKlasse); 
    // -> false
    ```

---
## (1) Ein Produkt

### (1.1) Definition
Schreib eine JavaScript Klasse `Produkt`, als Vorlage für Produkte in einem OnlineShop.

Die Klasse soll zwei Eigenschaften haben:
* ein `name` als Zeichenkette
* ein `preis` als Nummer

Der Konstruktor soll 2 Parameter nehmen, um diese Eigenschaften zu setzen.

Die Klasse soll zwei Methoden haben:
* `enthalteneSteuer()` - gib 16% des Preises als enthaltene Mehrwertsteuer zurück.
* `zuText()` - gib eine Zeichenkette mit dem Namen, Preis und der enthaltenen Steuer zurück. Wie:
    ```
    Premium Kaffee, 10.00€ (incl. 1.60€ MWSt.)
    ```

### (1.2) Benutzen:
Erstelle ein paar Instanzobjekte aus deiner Vorlagenklasse mit dem Schlüsselwort `new`

Beispiel:
* Adidas Laufschuhe for 120,50 € 
    ```javascript
    let schuhe = new Produkt("Adidas Laufschuhe", 120.50);
    ```
* Ein Malset for 15.99 €
* Ein Rasierset for 30.20 €
* Ein fünfer Pack Socken for 8.99 €

Gib die Produktbeschreibung aus indem du die `.zuText()` Methode deiner Instanzen aufrufst.

---
## (2) Der Warenkorb

### (2.1) Definition

Schreib eine Weitere Klasse `Warenkorb` als Vorlage für einen Einkaufswagen in einem OnlineShop.

Die Klasse soll eine Eigenschaft enthalten:
* `produkte`, als ein Feld (Array) von Produkten.

Bei Erstellen einer Instanz des Wwagens, wird er leer sein, also keine Produkte enthalten. Also ist das Array leer. Der Konstruktor wird also keine Parameter haben.

Für der Klasse zwei Methoden hinzu:
* `zumKorb(einProdukt)` die einen Parameter nimmt.
    * Lass die Methode prüfen, ob einProdukt eine Instanz der Klasse `Produkt` ist.
    * Nur wenn einProdukt eine Instanz der Klasse ist, dann füge sie in das Array von produkten hinzu.
* `auflisten()`, die keine Parameter nimmt.
    * Die Methode soll das Feld von Produkten durchlaufen.
    * für jedes Produkt im Warenkorb, rufe die `zuText()` Methode auf und gib die Rückgabe auf der Konsole aus.
    * **Bonus**: anstatt eine for-Schleife zu benutzen, denk über die Array-Methode array.forEach() nach; 

### (2.2) Benutzen
Erstelle eine Instanz deines Warenkorbs mit dem `new` Schlüsselwort

```javascript
let warenkorb = new Warenkorb();
```

Füge deine Produktinstanzen aus Aufgabe (1.2) deinem Warenkorb hinzu..

Beispiel:
```javascript
warenkorb.zumKorb(schuhe);
```

Ruf die `.auflisten()` Methode auf, um deinen Warenkorb auf der Konsole auszugeben.