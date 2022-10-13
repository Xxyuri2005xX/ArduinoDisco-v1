# arduinoDisco

![ItFlag](https://user-images.githubusercontent.com/84080587/194774644-66c6fa81-5d29-4b5c-a49f-c68afc953cde.png)

il seguente progetto riguarda la realizzazione di una discoteca intelligente che adatta la sua pista in base al numero di persone.
Le variabili e i commenti del progetto sono tutte in italiano.

lo sketch arduino (da caricare attraverso il suo IDE) sarà disponibile in 2 versioni (riconoscibili dal tag "- iso"): 
- Italiano - IT
- Inglese - EN

![EnFlag](https://user-images.githubusercontent.com/84080587/194774673-78c41fb4-463f-4ccd-86cf-5b8cb443272e.png)

the following project is about making an intelligent disco that adapts its track according to the number of people.
The project's variables and comments are all in italian.

the arduino sketch (to be loaded through its IDE) will be available in 2 versions (recognizable by the - "iso" tag): 
- Italian - IT
- English - EN

## Tinkercad project

![Tinkercad](https://user-images.githubusercontent.com/84080587/194775403-9f35a7ad-79f5-4fea-b5dc-288bc9b9d3bb.PNG)

## More led implementation

![ItFlag](https://user-images.githubusercontent.com/84080587/194774644-66c6fa81-5d29-4b5c-a49f-c68afc953cde.png)

Per implementare nuovi led RGB all'interno del progetto è necessario seguire i seguenti step:
- Implementare il nuovo led nel circuito (**!SONO NECESSARI 3 PIN MUNITI DI PWM PER IL FUNZIONAMENTO E UN COLLEGAMENTO AI 5V/MASSA IN BASE AL TIPO DI LED USATO**), per capire come collegare il led è sufficiente osservare lo schema tinkercad riportato sopra
- Successivamente prendere il seguente pezzo di codice e inserirlo tra le variabili dell'ultimo led RGB (nel caso del codice caricato qui su github led 2) e le altre variabili con questo frammento di codice in cui `X` rappresenta il numero identificativo del led (1,2,3,etc) e `x` il pin PWM (11,10,9,etc):
  ```yml
  //led rgb X
  int redX = x;
  int blueX = x;
  int greenX = x;```
- Successivamente bisogna dichiarare i 3 nuovi pin come OUTPUT nel setup dello sketch, quindi è necessario incollare il seguente frammento di codice sotto l'ultimo pinMode che dichiara OUTPUT prima di quelli di input, in cui X è il numero identificativo assegnato sopra:
  ```yml
  pinMode(redX, OUTPUT);
  pinMode(blueX, OUTPUT);
  pinMode(greenX, OUTPUT);
  ```
  - Uno degli ultimi step riguarda l'utilizzo del led nella funzione e la sua eventuale attivazione se si volesse usare con un numero x di persone. In questo caso Per implementare l'abilitazione del led è sufficiente trovare la parentesi graffa dell'ultimo if per il controllo del numero di persone (prima anche di quella di chiusura del loop e prima del sistema di debug) e inserire questo frammento di codice in cui `y` è il numero di persone che si desidera e `X` è il numero identificativo (vedi sopra):
  ```yml
  if(persone>=y) {
      rgbLedDisplay(redX, blueX, greenX, 
                  random(256), random(256), random(256));
    }
  ```
**!Nel caso si volesse implementare il led insieme ad un altro è sufficiente copiare la funzione senza l'if, si avvisa inoltre di NON cambiare gli ultimi 3 parametri che sono dei random number generator che creano numeri compresi tra 0 e 255 in modo da far cambiare colore al led in automatico**

![EnFlag](https://user-images.githubusercontent.com/84080587/194774673-78c41fb4-463f-4ccd-86cf-5b8cb443272e.png)

To implement new RGB leds within the project, the following steps must be followed:
- Implement the new led into the circuit (**!YOU NEED 3 PINS EQUIPPED WITH PWM FOR OPERATION AND A CONNECTION TO THE 5V/MASS BASED ON THE TYPE OF LED USED**), to understand how to connect the led just look at the tinkercad diagram above
- Next take the following piece of code and insert it between the variables of the last RGB led (in the case of the code uploaded here on github led 2) and the other variables with this code snippet where `X` represents the led's ID number (1,2,3,etc) and `x` the PWM pin (11,10,9,etc):
  ```yml
  //led rgb X
  int redX = x;
  int blueX = x;
  int greenX = x;```
- Next you need to declare the 3 new pins as OUTPUT in the sketch setup, then you need to paste the following code snippet under the last pinMode that declares OUTPUT before the input ones, where X is the ID number assigned above:
  ```yml
  pinMode(redX, OUTPUT);
  pinMode(blueX, OUTPUT);
  pinMode(greenX, OUTPUT);
  ```
- One of the last steps concerns the use of the LED in the function and its eventual activation if you wanted to use it with x number of people. In this case To implement enabling the led, simply find the brace in the last if for controlling the number of people (before even the loop closing one and before the debugging system) and insert this code snippet where `y` is the number of people you want and `X` is the identifying number (see above):
  ```yml
  if(people>=y) {
      rgbLedDisplay(redX, blueX, greenX, 
                  random(256), random(256), random(256));
    }
  ```
**!In case you want to implement the led together with another just copy the function without the if, also be warned NOT to change the last 3 parameters which are random number generators that create numbers between 0 and 255 so that the led changes color automatically**
