---
title: Пір’їнка
level: 2
author: 'Автор сценарію [Code Club UK](//codeclub.org.uk)'
Переклад : Хельге Астад
language: ua
---


# Вступ {.intro}

Зараз ми створимо власну версію гри __Flappy Bird__. Ви керуєте пташкою
__Пір’їнка’__ ved å trykke på mellomromtasten for å flakse med vingene. 
Вам потрібно утримувати Пір'їнку в повітрі і намагатись оминати труби

![Ілюстрація завершеної гри Flaxefugl](flaksefugl.png)


# Крок 1: Навчи Пір’їнку рухатися вниз {.activity}

*Ми почнемо з простого: створюємо аватар Пір’їнки та навчимо її рухатися вниз.*

## Контрольний список {.check}

- [ ] Почніть новий проект у Scratch. Для цього - видаліть кота, натиснувши на смітничок.

- [ ]Замініть Тло на пейзаж на Ваш вибір. Ми рекомендуємо обрати - Пустеля `Desert`.

- [ ] Додайте персонажа(спрей) Пірїн’ку. Вам потрібен персонаж з крили, піднятими вгору та
- [ ] опущеними вниз. Ми рекомендуємо обрати - Папуга `Parrot`.

- [ ] Перейменуйте персонажа на `Пір’їнка`.

- [ ] Задайте Пір’їнці сценарій дій, додавши цей скрипт:

  ```blocks
  коли клацне зелений прапорець
  перейти до x: (-50) y: (0)
  повторювати вічно
      змінити y з (-3)
  кінець
  ```

## Протестувати проект {.flag}

__Натисніть на зелений прапорець.__

- [ ] Starter Flakse midt på skjermen og faller mot bunnen?


# Крок 2: Навчи Пір’їнку рухатися вгору {.activity}

*Тепер ми хочемо, щоб Пір’їнка злітала вгору, коли ви натискаєте пробіл.*

## Контрольний список {.check}

- [ ] Відкрийте вкладення `Образи` і назвіть дві масті `Крила вгору` і 
  `Крила вниз`.

- [ ] Поверніться на вкладення `Код` та додайте відповідний скрипт поруч з попереднім: 

  ```blocks
  Коли натиснуто [пропуск v] натицнуто
  Змімти образ на [Крила вниз` v]
  повторити (10) разів
      змінити y з (6)
  кінець
  змінити образ [Крила вгору v]
  пожторити (10)
      змінити y на (6)
  повія
  ```

## Перевірка {.flag}

__Натисніть на зелений прапорець.__

- [ ] Чи можете ви керувати Пір’їнкою за допомогою клавіші пробілу?

- [ ] Чи помітили Ви, що якщо натискати пробіл кілька разів поспіль, то Пір’їнка
- [ ] іноді махає крилами лише один раз? Ми виправимо це на наступному кроці.


# Крок 3: Поліпшення контролю {.activity}

*Ми хочемо, щоб Пір’їнка реагував кожного разу, коли ми натискаємо пробіл. 
Але коли ми натискаємо пробіл, запускаються дві циклічні команди одна за одною. 
Якщо ми натискаємо пробіл до завершення цих двох циклів, нічого не відбувається. 
Щоб вирішити цю проблему, ми будемо використовувати змінну для підрахунку кількості махів, 
які нам потрібно зробити.*

## Контрольний список {.check}

- [ ] Створіть нову змінну і назвіть її `Пір’їнка`{.blockdata}.  Виберіть опцію, щоб змінна діяла тільки для цього
 ` персонажа`. Натисніть `ОК`. Сховати змінну, знявши галочку біля її назви.


- [ ] Тепер ми відмінимо сценарій, який запускається `при натисканні пробілу`{.blockevents}.
  Перетягніть `персонажа на цеглину «Крила вниз`{.blocklooks}
  щоб він і цеглини під ним від'єдналися. Відкладіть ці цеглини
  вбік. За мить вони нам знову знадобляться.

- [ ] Додайте ще один новий скрипт. Зверніть увагу, що цеглинки, які ви щойно додали
  на сторінку, можна використовувати `повторити до махати = 0`{.blockcontrol}:

  ```blocks
  коли клацнути зелений прапорець
  встановити [махати v] до [0]
  переодягнутися [крила вгору v]
  повторювати вічно
      повторити до <(махати) = [0]>
          змінити [махати v] з (-1)
          переодягнутися на [крила вниз v]
          повторити (10) разів
              змінитиy c (6)
          кінець
          переодягнутися на [крила вгору v]
          повторити на (10)
              зміна y 3 (6)
          кінець
      кінець
  кінець
  ```

- [ ] Наступний крок - додайте наступний сценарій до блоку `оли пробіл натиснутий`{.blockevents} який
залишився раніше:

  ```blocks
  коли [простірv] натиснуто
  змінити [махати v] з (1)
  ```

- [ ] Тепер ви маєте три різні сценарії для Пір’їнки.

## Перевірка {.flag}

__Натисніть на зелений прапорець.__

- [ ] Пір’їнка змахує крилами один раз під час кожного натискання пробілу?


# Крок 4:  Додайте перешкоди {.activity}

*Ми додамо деякі перешкоди, через які Пір’їнка може пролетіти.*

## Контрольний список {.check}

- [ ] Legg til en ny figur ved å klikke på *Tegn*-knappen.
- [ ] Додайте нову фігуру, натиснувши кнопку *маліовати*.

  ![Намалюйте нову форму](tegn-ny.png)

- [ ] Якщо на кнопці ліворуч під областю малювання написано `Перейти до векторної графіки`, натисніть цю кнопку.
- [ ] Klikk på `Zoom =` så du kan se hele tegneområdet.
- [ ] Натисніть `Режим приближення =` щоб ви могли побачити всю область малювання.

  ![Режим приближення =](zoom_eq.png)

- [ ] Клацніть піктограму `Прямокутникl`, ліворуч від області малювання ![Rektangel](rektangel.png). Velg farge på rektangelet som skal tegnes ved å klikke på `Fyll`. Velg en fin farge. Vi ønsker å gjøre omrisset av firkanten gjennomsiktig. Dette gjør vi ved å klikke på `Kant`, og klikke på ikonet helt nederst i farge-dialogen, med en rød skråstrek.

  ![fyll kant](fyll_kant.png)

- [ ] Tegn to bokser ved å klikke og dra i tegneområdet. Tegn én boks på toppen og én på bunnen av
  tegneflaten. Det skal se omtrent sånn ut:

  ![Bilde av et hinder for Flakse](pipe_design.png)

- [ ] Skyggelegg rørene. Dette gjør du ved å klikke `Velg` ![velg](velg.png). Deretter klikker du på firkanten som skal skyggelegges. Klikk på `Fyll`-ikonet over tegneområdet til venstre. I den nye dialogen som dukker opp, velg mellom forskjellige måter å skyggelegge på med de små ikonene i toppen av dialogen.

  ![Fyll gradering](fyll_gradering.png)

- [ ] Gi den nye figuren navnet `Rør`.


# Steg 5: Få rørene til å bevege seg{.activity}

*Nå skal vi få rørene til å flytte seg og gjøre høyden tilfeldig slik at vi får
 en hinderløype til Flakse.*

## Sjekkliste {.check}

- [ ] Klikk på `Rør`-figuren og velg `Kode`.

- [ ] Legg til disse to skriptene:

  ```blocks
  når grønt flagg klikkes
  skjul
  sett størrelse til (200)%
  gjenta for alltid
      lag klon av [meg v]
      vent (2) sekunder
  slutt

  når jeg starter som klon
  gå til x: (240) y: (tilfeldig tall fra (-80) til (80))
  vis
  gjenta (120) ganger
      endre x med (-4)
  slutt
  slett denne klonen
  ```

## Test prosjektet {.flag}

__Klikk det grønne flagget.__

- [ ] Kommer det mange rør flygende mot Flakse?

- [ ] Har rørene åpninger til å fly gjennom?

- [ ] Om du synes det er vanskelig å fly Flakse gjennom åpningene, kan du for
  eksempel endre på åpningen mellom rørene med tegneverktøyet. En annen mulighet
  er å lage Flakse mindre.


# Steg 6: Finn ut om Flakse kræsjer med rørene {.activity}

*For at spillet skal bli vanskelig må spilleren styre Flakse gjennom åpningene
 mellom rørene uten å komme borti hverken rør eller kanten av skjermen. Vi skal
 legge til noen klosser som merker om Flakse kræsjer.*

## Sjekkliste {.check}

- [ ] Vi legger til en lyd som vi kan spille når Flakse kræsjer. Klikk på
  `Flakse`-figuren og så på fanen `Lyder`.

- [ ] Klikk på `Velg en lyd`-ikonet, nederst til venstre i vinduet.

- [ ] Velg en kræsjelyd for `Flakse`.  `Screech` er en kul lyd.

- [ ] Klikk deg tilbake til `Kode`-fanen.

- [ ] Legg til dette skriptet på Flakse:

  ```blocks
  når grønt flagg klikkes
  vent til <<berører [kant v]?> eller <berører [Rør v]?>>
  start lyden [screech v]
  si [Du tapte!]
  send melding [Tap v]
  stopp [andre skript i figuren v] :: control
  ```

- [ ] Klikk så på `Rør`-figuren og legg til dette skriptet:

  ```blocks
  når jeg mottar [Tap v]
  stopp [andre skript i figuren v] :: control
  ```

## Test prosjektet {.flag}

__Klikk det grønne flagget.__

- [ ] Stopper spillet hvis Flakse kommer borti et rør eller kanten av
  brettet?


# Steg 7: Legg til poeng {.activity}

*Spilleren skal score ett poeng hver gang Flakse flyr gjennom en røråpning.*

## Sjekkliste {.check}

- [ ] Vi legger til en lyd hver gang Flakse scorer ett poeng. Klikk på
  `Rør`-figuren og legg til en lyd. `Bird` er et lurt valg.

- [ ] Gå tilbake til `Kode`-fanen.

- [ ] Lag en ny variabel som skal gjelde `For alle figurer`. Kall den
  `poeng`{.blockdata}.

- [ ] Legg til et skript som setter poengene til 0 når det grønne flagget
  klikkes. Dette klarer du selv!

- [ ] Legg så til dette skriptet på `Rør`:

  ```blocks
  når jeg starter som klon
  vent til <(x-posisjon) < ([x-posisjon v] av [Flakse v])>
  endre [poeng v] med (1)
  start lyden [bird v]
  ```

## Test prosjektet {.flag}

__Klikk det grønne flagget.__

- [ ] Scorer du poeng når Flakse flyr forbi en åpning mellom rørene?

- [ ] Hvordan kan du lage dette spillet lettere eller vanskeligere?

## Lagre prosjektet ditt {.save}

Supert, du har laget ferdig din egen enkle versjon av Flappy
Bird-spillet.

Her er noen flere ting du kan prøve:

## Utfordring 1: Legg til tyngdekraft {.challenge}

Når noe faller på grunn av tyngdekraft øker farten jo lenger fallet
varer. Vi skal prøve å etterligne denne måten å falle på.

- [ ] Legg til en ny variabel for `Flakse` som heter `løft`{.blockdata}.
  Variablen skal gjelde for `For denne figuren`.

- [ ] Endre Flakses falleskript:

  ```blocks
  når grønt flagg klikkes
  sett [løft v] til [0]
  gå til x: (-50) y: (0)
  gjenta for alltid
      endre y med (løft)
      endre [løft v] med (-0.2)
  slutt
  ```

- [ ] Deretter må vi endre Flakses flakseskript:

  ```blocks
  når grønt flagg klikkes
  sett [flaks v] til [0]
  bytt drakt til [Vinger opp v]
  gjenta for alltid
      gjenta til <(flaks) = [0]>
          endre [flaks v] med (-1)
          bytt drakt til [Vinger ned v]
          endre [løft v] med (4)
          vent (0.1) sekunder
          bytt drakt til [Vinger opp v]
          vent (0.1) sekunder
      slutt
  slutt
  ```

## Test prosjektet {.flag}

__Klikk det grønne flagget.__

- [ ] Faller Flakse fortere jo lenger han detter?

## Utfordring 2: Fall ut av skjermen {.challenge}

Når spilleren taper vil vi at Flakse faller ned og ut av skjermen.

- [ ] Bytt ut `send meldingen Tap`{.blockevents}-klossen med `send meldingen
  Fall`{.blockevents} i skriptet som merker når Flakse kræsjer i kanten eller i
  et rør. Slett `stopp`{.blockcontrol}-klossen på slutten av skriptet.

- [ ] Legg til disse nye skriptene på `Flakse`-figuren:

  ```blocks
  når jeg mottar [Fall v]
  gjenta for alltid
      snu @turnRight (5) grader
  slutt

  når jeg mottar [Fall v]
  gjenta til <(y-posisjon) < [-180]>
      endre y med (løft)
      endre [løft v] med (-0.2)
  slutt
  skjul
  send melding [Tap v]
  stopp [andre skript i figuren v] :: control
  ```

- [ ] Du må også legge til en `vis`{.blocklooks}-kloss samt sette Flakses
  retning når spillet starter på nytt.

## Test prosjektet {.flag}

__Klikk det grønne flagget.__

- [ ] Faller Flakse ut av skjermen når han treffer et rør?

- [ ] Flyr Flakse riktig vei når spillet starter igjen?


## Lagre prosjektet ditt {.save}

__Gratulerer, du er ferdig med spillet! Hva er rekorden din?__

Ikke glem å dele spillet med vennene dine. Trykk på `Legg ut` for at andre skal
få prøve!
