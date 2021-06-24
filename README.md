# Opravný termín \[60b], 24.6.2021 14:00
B-OOP 2021

Vytvorte oknovú aplikáciu, ktorá umožní používateľovi "pečiatkovať" dva tvary a spájať ich pomocou čiar. Aplikácia bude mať nasledovnú funkcionalitu (40 bodov):

1. Vytvorenie hlavného okna, ktoré bude obsahovať Ovládacie prvky a Kresliacu plochu \[4b].
2. Sfunkčnenie ovládacích prvkov pomocou Listenerov \[5b].
3. "Pečiatkovanie" dvoch tvarov: strom a dom \[10b].
4. Prepájanie tvarov pomocou čiar \[15b].
5. Zmena farieb počas kreslenia a vrstvenie elementov \[5b].
6. Zatvorenie aplikácie cez tlačidlo na zatvorenie aplikácie poskytnuté operačným systémom \[1b].

## Podrobný popis k bodu 1:

Väčšinu plochy okna bude zaberať Kresliaca plocha. V hornej časti okna sa budú nachádzať Ovládacie
prvky. Ovládacie prvky budú tvoriť: [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) “Strom”, [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) “Dom”, [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) “Cesta” a [JLabel](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JLabel.html). Každý z týchto prvkov musí zaberať štvrtinu celkového miesta vyhradeného pre ovládacie prvky.

## Podrobný popis k bodu 2:

Po spustení programu je zvolený ľubovoľný z módov "Dom" alebo "Strom". Aktuálne zvolený mód sa zobrazuje ako text na [JLabel](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JLabel.html) elemente na ovládacom paneli ("Dom", "Strom", "Cesta"). Aktívny mód sa zmení iba kliknutím na príslušný [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) na ovládacom panely. Panel má nastavenú farbu pozadia podľa aktuálkne zvolenej farby (pozri bod 5).

## Podrobný popis k bodu 3:

Keď je zvolený jeden z módov "Dom" alebo "Strom", tak používateľ má možnosť pridávať príslušné tvary na kresliacu plochu. Kreslenie prebieha formou pečiatkovania, teda po kliknutí sa na mieste na ktoré sa kliklo vykreslí zvolený tvar \[2b]. Tvar sa vykresľuje tak, že jeho stred sa nachádza v mieste kam klikla myš \[3b]. Tvary nakreslené v minulosti zostávajú po kliknutí na kresliacej ploche. Tvary majú fixný rozmer 50\*50px. Na pozícii myši sa zobrazuje polopriehľadný náhľad aktuálne zvoleného tvaru/pečiatky \[5b]. Tvar aj náhľad sa vykresľuje aktuálne zvolenou farbou (pozri bod 5). Pokiaľ funguje vykresľovanie iba jedného tvaru je úloha hodnotenámaximálne polovičným počtom bodov. Tvary majú mať nasledovné proporcie:

![image](./strom.svg)

## Podrobný popis k bodu 4:

Keď je zvolený mód "Cesta" je možné prepájať domy a stromy čiarami. Cestu (čiaru) je možné začať kresliť stlačením myši nad nejakým nakresleným tvarom. Následne sa pri ťahaní myši kreslí čiara medzi stredom tvaru a aktuálnou pozíciou myši. Pokiaľ je tlačidlo myši pustené nad prázdnou plochou, čiara zmizne. Pokiaľ je tlačidlo myši pustené nad tvar opačného druhu, ako je začiatok čiary, tak sa kreslenie čiary dokončí a čiara bude spájať stredy nakreslených tvarov \[10b]. Čiarami je možné spájať iba tvary opačného druhu (dom - strom, strom - dom) \[5b]. Čiary sa vždy vykresľujú čiernou farbou.

Na detekciu kliknutia myši na tvar môžete použiť napríklad metódu [contains](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/Shape.html#contains(double,double)) triedy [Shape](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/Shape.html)

## Podrobný popis k bodu 5:

Program obsahuje minimálne 3 farby v nejakom fixnom poradí (napr. červená > modrá > zelená). Na začiatku programu je zvolená prvá farba z poradia (tým pádom je takou farbou podfarbený aj label). Po nakreslení ľubovoľného z tvarou sa aktuálna farba zmení na nasledujúcu v poradí. Po zmene farby sa zmení farba Label-u podľa aktuálnej farby. Zmena farby ovplyvňuje len nové geometrické tvary, už nakreslené geometrické tvary si musia zachovať svoju farbu! 

Poradie vykreslovania prvkov musí byť také, že: Tvary > Čiari > Náhľad zvoleného tvaru (ak je zvolený mód Dom alebo Strom) 

## Hodnotenie

Projekt obsahuje github pipeline, ktorá kontroluje skompilovateľnosť programu. **Pokiaľ program nie je skompilovateľný nebude hodnotený a skúška bude hodnotená 0b!**

**Pokiaľ budete počas skúšky pristihnutý pri podvádzaní, alebo bude váš kód vykazovať príliš veľkú podobnosť s kódom iných študentov, bude skúška hodnotená 0 bodmi!**

Okrem funkcionality budú hodnotené aj princípy Objektovo orientovaného programovania (20 bodov), najmä:

* správne využitie modifikátory prístupu, \[3b]
* vhodné pomenovanie tried a metód, \[3b]
* vhodné využitie dedenia a polymorfizmu, \[3b]
* vhodné použitie výnimiek na ošetrenie nedovoleného správania (nehádzať a nezachytávať všeobecnú triedu Exception), \[3b]
* nepoužitie vnorených tried (nested class), \[2b]
* nepoužitie statických metód ani nekonštantných statických premenných, \[3b]
* nepoužitie duplicitných kódov \[3b]

Pokiaľ vaše riešenie neobsahuje dostatok implementácie je možné za OOP získať maximálne \[10b]. 

## Odovzdanie

Vypracovanie skúšky odovzdajte cez Github classroom do miesta odovzdania nato určenom. Odovzdáva sa obsah celého projektu. Na vypracovanie písomky je vyhradený čas 3 hodiny.

# Exam OT \[60pts], 24.6.2021 14:00
B-OOP 2021

Your task is to create a java window application. The application allows the user to draw and move a given shape. The application has the following functionality (40 points):

1. Creation of the main window, that will contain control elements and a drawing area \[5pts].
2. Drawing of one shape: a tree \[15pts].
3. Moving of the drawn shapes \[15pts].
4. Selection of the drawing color through a [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) \[4pts].
5. Closing the application with the "close window" button provided by the operating system \[1pt].

## Description for bullet point 1:

Most of the window area will be covered by the drawing area. THe bottom part of the window will contain the control elements. The control elements consist of: [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) "Tree", [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) "Move", [JButton](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JButton.html) "Next color" and a [JLabel](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/JLabel.html). Each of these elements should cover a fourth of the available space for control elements.

## Description for bullet point 2:

By pressing the appropriate button we select drawing of the TREE [5pts]. After pressing the left mouse button and draging the mouse the selected shape will begin drawing on to the drawing area. The label (from the control elements) will have its text changed to **DRAWING**. Based on the current position of the mouse, the width and height of the drawn shape will be dynamically adjusted. After letting go of the left mouse button the drawing of the shape will complete, i.e. its position and size fill be fixed. The drawn shape must remain on the drawing area after drawing additional shapes. Each shape must maintain its color (the color will change based on a button, see bullet point 4). The tree shape must maintain the proportions depicted on the image bellow.

![image](./strom.svg)

**Note:** When drawing (dragging the mouse) a shape the position and direction of the mouse must be considered. You must consider how to calculate the position and size of the selected shape. If you implement the drawing of the shape into all four direction the mouse can be dragged in (top right to bottom left, bottom left to top right, top left to bottom right, bottom right to top left) you will receive the full [10pts]. If you do not implement all four possibilities you will be able to recive at most a half of the available points (max 5pts).

## Description for bullet point 3:

By pressing the appropriate button the **MOVING** mode will be selected and the appropriate text of the label (in the controll panel) will be set. After pressing the left mouse button on an already drawn shape and then dragging the mouse, the selected shape will move with the mouse. After letting go of the left mouse button the movement of the shape will finish i.e. the shape will remain fixed in its new place. THe dragged shape will be drawn only at the position of the mouse and will not remain at its original location.

**Note:** When moving (dragging the mouse) of a selected shape you must consider the relative position of the mouse to the moved shape. For implementing the dragging in any way at most 10pts can be received. If the movement is performed relative to the click location of the mouse (i.e. when dragging from the center of the shape the mouse remains in the center of the shape during the movement) you will receive the full 15pts.

You can use the [contains](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/Shape.html#contains(double,double)) method of the [Shape](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/Shape.html) class to determine whether the mouse was pressed inside of a shape.

## Description for bullet point 4:

Among the control elements the Button "Next color" will serve the purpose of selecting the drawing color. The Lable will display the currently selected color. The program allows the selection of at least 3 different colors in some fixed order (e.g. red > blue > green). By pressing the button the selected color will change to the next color in the ordering. If the currently selected color is the last color in the ordering, the next color is the first color of the ordering (i.e. red > blue > green > red > ...). The currently drawn shapes have the currently selected color. You can choose the available colors freely, but they must be clearly visible on the drawing area. After selecting a color the color of the Label will change based on the currently selected color. The change of the color affect only new shapes, the shapes that are already drawn must maintain their color!

## Grading

The project contains a github pipeline, that checks whether it can be compiled or not. **If the program cannot be compiled it will not be graded and 0 points will be received for the exam!**.

**If you are caught cheating during the exam, or if the source code handed in by you will have a suspicious amount of similarities with the code of other students 0 points will be received for the exam!**

Appart from the functionality, the principles of Object-Oriented Programming will be graded as well (20 pts), pay close attention especially to:

* correct usage of access modifiers, \[3pts]
* appropriate naming of classes and methods, \[3pts]
* appropriate usage of inheritance and polymorphism, \[3pts]
* appropriate usage of exceptions when handling undesired behavior (do not catch or throw the instances of the generic Exception class), \[3pts]
* don't use nested classes, \[2pts]
* don't use static methods, or non-constant static variables, \[3pts]
* don't have code duplication \[3pts]

## Odovzdanie

Vypracovanie skúšky odovzdajte cez Github classroom do miesta odovzdania nato určenom. Odovzdáva sa obsah celého projektu. Na vypracovanie písomky je vyhradený čas 3 hodiny.

## Handing in the assigment

Hand in the assignment into your Github classroom repository for this exam. Hand in the entire project. You have 3 hours to complete the exam.
