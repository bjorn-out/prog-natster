# Deeltjes in een doos

In een doos (afmeting $$0 \leq x \leq 1$$ en $$0 \leq y \leq 1$$) worden op een bepaalde plek ($$x_{bron}, y_{bron}$$) = (0,25;0,75) een aantal deeltjes weggeschoten in een willekeurige richting en snelheid. Voor elk deeltje $$i$$ geldt:

   - snelheid $$(v_{i}): 0 < v_{i} < 0.10$$
   - hoek $$(\alpha_{i}): 0 < \alpha_{i} < 2\pi$$
   
<p align="center">
![](ParticlesInABox_box.png){: style="width:50%"}
</p>

We gaan in deze opdracht de positie van een groot aantal deeltjes volgen. Hoewel we in het begin de aanname zullen maken dat de deeltjes niet botsen (dat maakt de simulatie veel  makkelijker), zullen we aan het eind wat realisme toevoegen en de deeltjes laten botsen.

## Deel 1: niet-botsende deeltjes

Onze aannames in dit deel van de opdracht:

   1.  Er worden 1000 deeltjes geproduceerd
   
   2.  De deeltjes ketsen elastisch tegen de wanden en kunnen de doos niet uit

   3.  De deeltjes hebben geen afmeting en kunnen niet botsen

   4.  De doos is gesloten
   
Algemene aanpak van de simulatie:

##### stap 1: genereer een beginsituatie
  
  Elk deeltje wordt gekarakteriseerd door vier getallen: de x-positie (x), de y-positie (y) en de snelheid in de x-richting (vx) en de y-richting (vy). Maak daarom in het begin van je programma vier lijsten aan die de posities en snelheden van alle deeltjes bevatten.
  
**Tips:**

   - Als je in het begin (t=0) de random snelheid en richting hebt gekozen voor het deeltje kan je die gelijk om schrijven in termen van vx en vy. Deze snelheden zullen niet meer veranderen (bedenk waarom niet), tenzij het deeltje tegen de wand botst natuurlijk.
   
   - begin niet gelijk met 1000 deeltjes, maar volg een enkel deeltje in de tijd om te kijken of het deeltje zich wel gedraagt zoals je denkt dat je het geprogrammeerd hebt: ketst het bijvoorbeeld wel (goed) af van de wanden etc.

   - Hoewel het helemaal in het begin van het programma handig is om het pad van een deeltje te volgen (botst hij wel netjes terug van de wanden) is het **niet** handig om in je programma voor elk deeltje de positie en snelheid bij als functie van de tijd bij te houden. De vier lijsten die we eerder genoemd hebben bevatten alleen de posities en snelheden op een enkel tijdstip. 

##### stap 2: maak stapjes in de tijd

Omdat elk deeltje een snelheid heeft zal zijn positie veranderen in de tijd. Maak kleine stapjes in de tijd ($$\Delta t$$) en bereken op welke nieuwe positie het deeltje terecht zal komen. Gebruik hiervoor, als voorbeeld voor de positie in de x-richting): 

  $$x_i(t+\Delta_t) = x_i(t) + v_x,i(t)\Delta t$$ 

De snelheid in de x-richting zal onveranderd blijven, tenzij het deeltje tegen de wand botst natuurlijk. Bedenk zelf wat er moet gebeuren als het deeltje op een positie buiten de doos terechtkomt. De deeltjes mogen de doos immers niet uit.


##### Opdracht 1: gesloten doos

Schrijf een programma `deeltjes_deel1.py` dat 100 deeltjes produceert en de simulatie in de tijd laat lopen gedurende een groot aantal stappen. Het programma moet twee grafieken produceren:
 
   - Een grafiek van het aantal deeltjes aan de rechterkant van de doos ($$x_i > 0,5$$) als functie van de tijd.

   - Een grafiek van de gemiddelde afstand tussen de deeltjes als functie van de tijd.

##### Opdracht 2: doos met een gat

Stel nou dat er een gat in de doos zit ($$y_{gat} = 0$$ en $$0,8 \leq x_{gat} \leq 0,9$$). Het is dan mogelijk dat deeltjes uit de doos ontsnappen. Het tijdstip waarop (meer dan) de helft (of meer) van de deeltjes noemen we $$t_{/frac{1}{2}}$$.

Schrijf een programma `deeltjes_deel2.py` dat een aantal simulaties runt en daarvan de  gemiddelde tijd uitrekent waarop in een simulatie (meer dan) de helft van de deeltjes uit de doos verdwenen zijn. Gebruik 100 simulaties die elk 100 deeltjes bevatten.

Probeer ook zonder computerprogramma een schatting te geven. Hoe zou je dat aanpakken?

## Deel 2: botsende deeltjes

Er zijn verschillende mogelijkheden om deze simulatie uit te breiden met meer real-
isme. Het visualiseren van een simulatie is erg leuk en interessant omdat het je meer
inzicht geeft in mogelijke programmeerfouten en fenomenen die soms niet gelijk op-
vallen als je naar de vergelijkingen zelf kijkt. We zullen de deeltjes ook een 'echte'
afmeting geven en de deeltjes te laten botsen.

![](collidingballs_4.gif){: style="width:50%"}{:.inline}

Je mag in deze opdracht zelf weten waar je de deeltjes neerzet in de doos op het startmoment. Omdat de animatie (nu met circels i.p.v puntjes zoals eerder in de opgave) net even lastiger is hebben we een voorbeeld template aangeleverd dat jullie zelf aan kunnen passen: [animation_template_circles.py](https://www.nikhef.nl/~ivov/Python/DeeltjesInDoos/animation_template_circles.py)

##### Opdracht 3: deeltjes met afmeting (zonder botsen)

Schrijf een programma `deeltjes_deel3.py` om tien deeltjes door de doos te zien bewegen als functie van de tijd. Gebruik as basis het simpele voorbeeld van twee om elkaar draaiende balletjes uit het voorbeeld.

Geef de deeltjes een afmeting en laat ze netjes van de wand ketsen als de rand van het deeltje de wand raakt (en dus niet het centrum van het deeltje). 


##### Opdracht 4: deeltjes met afmeting (met botsen)

Schrijf een programma `deeltjes_deel4.py` dat gebaseerd is op die van opdracht 3, maar waarbij nu de deeltjes (met afmeting) realistisch botsen. Handig hierbij is misschien de afleiding van de botsingskinematica 
[2-dimensional elastic collisions without trigonometry](http://www.vobarian.com/collisions/2dcollisions2.pdf).



## Checkpy

Er is voor deze opdracht geen checkpy oplossing aanwezig. You're on your own.