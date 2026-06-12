# DESIGN.md — Design System Universale

> **Versione**: 3.0  
> **Ambito**: Siti web, Web App, Dashboard, Mobile App  
> **Lingue supportate**: Italiano, Inglese, multilingua  
> **Compatibilità**: Claude Design, Stitch, Figma, dev handoff  
> **Ultimo aggiornamento**: 2026-04-23

---

## INDICE

```
01. Filosofia e Principi
02. Design Tokens — Colori
03. Design Tokens — Tipografia
04. Design Tokens — Spaziatura e Griglia
05. Design Tokens — Ombre, Raggi, Bordi
06. Design Tokens — Movimento e Animazioni
07. Design Tokens — Z-Index e Layering
08. Breakpoint e Responsive
09. Sistema di Griglia e Layout
10. Regole Tipografiche Avanzate
11. Internazionalizzazione (i18n) e Multilingua
12. Inventario Componenti
13. Stati dei Componenti
14. Proprietà dei Componenti
15. Pattern di Navigazione
16. Pattern per Dashboard
17. Pattern per Form e Input
18. Pattern per Tabelle e Dati
19. Pattern per Feedback e Notifiche
20. Pattern per Contenuti e Card
21. Iconografia
22. Immagini e Media
23. Accessibilità (WCAG 2.2 AA)
24. Dark Mode
25. Prototipazione — Regole Generali
26. Prototipazione — Flussi e Struttura
27. Prototipazione — Interazioni e Transizioni
28. Prototipazione — Stitch Specifico
29. Prototipazione — Claude Design Specifico
30. Naming Convention
31. Struttura File e Pagine
32. Checklist QA Pre-Handoff
33. Anti-Pattern — Cosa NON Fare
34. Glossario
```

---

## 01. Filosofia e Principi

```
PRINCIPIO                         DESCRIZIONE
─────────────────────────────────────────────────────────────────────────
Coerenza prima di tutto           Ogni decisione visiva nasce da un token.
                                  Mai valori arbitrari.

Chiarezza sopra la decorazione    L'interfaccia deve comunicare, non impressionare.
                                  La bellezza nasce dalla funzione.

Accessibilità non negoziabile     WCAG 2.2 AA è il minimo. Non è un'opzione,
                                  è un requisito strutturale.

Mobile-first, desktop-enhanced    Si progetta dal vincolo più stretto.
                                  Il desktop estende, non riduce.

Token-driven                      Nessun colore, spaziatura, ombra o dimensione
                                  esiste fuori dal sistema di token.

Componenti, non pagine            Si progettano componenti modulari.
                                  Le pagine sono composizioni di componenti.

Internazionale per default        Ogni componente deve funzionare in italiano,
                                  inglese, tedesco, arabo (RTL), giapponese.
                                  Mai assumere una sola lingua.

Stato completo                    Un componente senza tutti i suoi stati
                                  (hover, focus, error, disabled, loading)
                                  è un componente incompleto.

Prototipazione realistica         Usare dati reali, non lorem ipsum.
                                  Testare con stringhe lunghe e corte.
                                  Testare con contenuti in più lingue.
```

---

## 02. Design Tokens — Colori

### 02.1 Scala Primitiva

```
NON usare mai questi direttamente nei componenti.
Servono solo come riferimento per i token semantici.

GRAY                              BRAND
gray.0      #FFFFFF               brand.50    #EFF6FF
gray.25     #FCFCFD               brand.100   #DBEAFE
gray.50     #F9FAFB               brand.200   #BFDBFE
gray.100    #F3F4F6               brand.300   #93C5FD
gray.200    #E5E7EB               brand.400   #60A5FA
gray.300    #D1D5DB               brand.500   #3B82F6
gray.400    #9CA3AF               brand.600   #2563EB
gray.500    #6B7280               brand.700   #1D4ED8
gray.600    #4B5563               brand.800   #1E40AF
gray.700    #374151               brand.900   #1E3A8A
gray.800    #1F2937               brand.950   #172554
gray.900    #111827
gray.950    #030712

ACCENT                            NEUTRALI CALDI (opzionale)
accent.50   #FFF7ED               warm.50     #FAFAF9
accent.100  #FFEDD5               warm.100    #F5F5F4
accent.200  #FED7AA               warm.200    #E7E5E4
accent.300  #FDBA74               warm.300    #D6D3D1
accent.400  #FB923C               warm.400    #A8A29E
accent.500  #F97316               warm.500    #78716C
accent.600  #EA580C               warm.600    #57534E
accent.700  #C2410C               warm.700    #44403C
accent.800  #9A3412               warm.800    #292524
accent.900  #7C2D12               warm.900    #1C1917
```

### 02.2 Token Semantici — Tema Chiaro

```
SUPERFICI
surface.page              gray.0        Sfondo pagina principale
surface.default           gray.0        Sfondo card e container
surface.subtle            gray.50       Sfondo secondario, righe alternate
surface.muted             gray.100      Sfondo input disabilitati, skeleton
surface.inset             gray.100      Sfondo aree incassate (sidebar, well)
surface.raised            gray.0        Card elevata (con shadow)
surface.overlay           gray.0        Modal, popover, dropdown
surface.inverse           gray.900      Superfici invertite (tooltip scuro)
surface.brand             brand.500     CTA principale, header brand
surface.brand-subtle      brand.50      Badge brand, background highlight

TESTO
text.primary              gray.900      Titoli e body principale
text.secondary            gray.600      Testo descrittivo, caption
text.tertiary             gray.400      Placeholder, hint
text.disabled             gray.300      Testo disabilitato
text.inverse              gray.0        Testo su superfici scure
text.brand                brand.600     Link, label brand
text.success              #15803D       Messaggi di successo
text.warning              #A16207       Messaggi di attenzione
text.error                #B91C1C       Messaggi di errore
text.info                 #1D4ED8       Messaggi informativi

BORDI
border.default            gray.200      Bordi standard
border.strong             gray.300      Bordi enfatizzati
border.subtle             gray.100      Bordi leggeri (separatori)
border.focus              brand.500     Ring di focus
border.error              #DC2626       Bordo campo in errore
border.success            #16A34A       Bordo campo valido
border.brand              brand.500     Bordo evidenziato brand
border.disabled           gray.200      Bordo disabilitato

ICONE
icon.default              gray.500      Icone standard
icon.strong               gray.700      Icone enfatizzate
icon.subtle               gray.400      Icone secondarie
icon.disabled             gray.300      Icone disabilitate
icon.brand                brand.600     Icone brand
icon.inverse              gray.0        Icone su sfondo scuro
icon.success              #16A34A
icon.warning              #EAB308
icon.error                #DC2626
icon.info                 #2563EB

INTERAZIONI
interactive.default       brand.600     Colore interattivo base
interactive.hover         brand.700     Hover su elementi interattivi
interactive.active        brand.800     Stato premuto
interactive.focus-ring    brand.200     Anello di focus (con opacità)
interactive.disabled      gray.300      Stato disabilitato
interactive.destructive   #DC2626       Azioni distruttive
interactive.destr-hover   #B91C1C       Hover azioni distruttive
```

### 02.3 Colori Funzionali

```
STATUS          BACKGROUND       BORDER          TEXT            ICON
success         #F0FDF4          #BBF7D0         #15803D         #16A34A
warning         #FEFCE8          #FEF08A         #A16207         #EAB308
error           #FEF2F2          #FECACA         #B91C1C         #DC2626
info            #EFF6FF          #BFDBFE         #1D4ED8         #2563EB
neutral         gray.50          gray.200        gray.600        gray.500
```

---

## 03. Design Tokens — Tipografia

### 03.1 Font Stack

```
RUOLO             FONT PRIMARIO             FALLBACK
display           "Plus Jakarta Sans"       "DM Sans", system-ui, sans-serif
heading           "Plus Jakarta Sans"       "DM Sans", system-ui, sans-serif
body              "DM Sans"                 "Plus Jakarta Sans", system-ui, sans-serif
mono              "JetBrains Mono"          "Fira Code", "SF Mono", monospace

NOTA: Scegliere font con supporto esteso per:
  - Caratteri latini estesi (àèéìòù, ñ, ü, ø, ß)
  - Cirillico (se necessario)
  - Set completo di pesi (400–700 minimo)

PER LINGUE CJK (cinese, giapponese, coreano):
  font.cjk: "Noto Sans JP", "Noto Sans SC", sans-serif

PER LINGUE RTL (arabo, ebraico):
  font.rtl: "Noto Sans Arabic", "IBM Plex Sans Arabic", sans-serif
```

### 03.2 Scala Dimensioni

```
TOKEN              REM        PX      USO TIPICO
font.size.2xs      0.625      10      Badge numerici molto piccoli (uso raro)
font.size.xs       0.75       12      Caption, label secondarie, timestamp
font.size.sm       0.875      14      Label, body compatto, helper text
font.size.base     1.0        16      Body principale, paragrafi
font.size.md       1.125      18      Body large, lead text
font.size.lg       1.25       20      Heading 5, sottotitoli
font.size.xl       1.5        24      Heading 4
font.size.2xl      1.875      30      Heading 3
font.size.3xl      2.25       36      Heading 2
font.size.4xl      3.0        48      Heading 1
font.size.5xl      3.75       60      Display heading
font.size.6xl      4.5        72      Hero display (uso raro)
```

### 03.3 Pesi

```
font.weight.regular     400       Body, paragrafi
font.weight.medium      500       Label, caption enfatizzate, nav link
font.weight.semibold    600       Heading, sottotitoli, pulsanti
font.weight.bold        700       Display, enfasi forte, stat number
```

### 03.4 Interlinea

```
font.leading.none       1.0       Stat numbers, display isolati
font.leading.tight      1.2       Heading grandi (4xl+)
font.leading.snug       1.35      Heading medi (2xl–3xl)
font.leading.normal     1.5       Body, paragrafi standard
font.leading.relaxed    1.65      Body piccolo, caption, testo lungo
font.leading.loose      1.8       Massima leggibilità (uso raro)
```

### 03.5 Tracking (Letter Spacing)

```
font.tracking.tighter   -0.02em   Display grandi (5xl+)
font.tracking.tight     -0.01em   Heading (3xl–4xl)
font.tracking.normal    0em       Body, testo standard
font.tracking.wide      0.025em   Overline, label
font.tracking.wider     0.05em    Overline maiuscolo
font.tracking.widest    0.08em    Badge, tag, stato
```

### 03.6 Stili Composti

```
NOME                  FONT         SIZE    WEIGHT     LEADING    TRACKING
text.display-hero     display      6xl     bold       tight      tighter
text.display-xl       display      5xl     bold       tight      tighter
text.display-lg       display      4xl     bold       tight      tight
text.heading-1        heading      3xl     bold       snug       tight
text.heading-2        heading      2xl     semibold   snug       normal
text.heading-3        heading      xl      semibold   snug       normal
text.heading-4        heading      lg      semibold   normal     normal
text.heading-5        heading      base    semibold   normal     normal
text.body-xl          body         md      regular    relaxed    normal
text.body-lg          body         base    regular    normal     normal
text.body-base        body         sm      regular    normal     normal
text.body-sm          body         xs      regular    relaxed    normal
text.label-lg         body         base    medium     tight      normal
text.label-base       body         sm      medium     tight      normal
text.label-sm         body         xs      medium     tight      wide
text.caption          body         xs      regular    relaxed    normal
text.overline         body         xs      semibold   tight      widest     + uppercase
text.code-lg          mono         base    regular    normal     normal
text.code-base        mono         sm      regular    normal     normal
text.code-sm          mono         xs      regular    relaxed    normal
text.stat-xl          heading      5xl     bold       none       tighter
text.stat-lg          heading      4xl     bold       none       tighter
text.stat-base        heading      3xl     bold       none       tight
```

---

## 04. Design Tokens — Spaziatura e Griglia

### 04.1 Scala Spaziatura

```
TOKEN       PX      REM       USO TIPICO
space.0     0       0
space.0.5   2       0.125     Micro-adjustment (bordi, offset)
space.1     4       0.25      Gap icona-testo inline, padding badge
space.1.5   6       0.375     Padding interno badge, chip
space.2     8       0.5       Gap minimo tra elementi correlati
space.2.5   10      0.625     
space.3     12      0.75      Padding interno piccolo, gap form label
space.4     16      1.0       Padding standard, gap tra elementi
space.5     20      1.25      Padding interno card compatta
space.6     24      1.5       Padding card standard, gap sezioni interne
space.8     32      2.0       Padding card large, margine tra blocchi
space.10    40      2.5       Gap tra sezioni interne
space.12    48      3.0       Separazione sezioni pagina
space.16    64      4.0       Margine verticale tra sezioni principali
space.20    80      5.0       Spaziatura hero section
space.24    96      6.0       Spaziatura sezioni grandi
space.32    128     8.0       Massimo spazio tra macro-sezioni
space.40    160     10.0      Padding hero verticale (desktop)
space.48    192     12.0      Uso raro, aree molto grandi
```

### 04.2 Spaziatura Semantica

```
TOKEN                          VALORE         CONTESTO
spacing.page-padding-x         space.4        Padding orizzontale mobile
spacing.page-padding-x-md      space.8        Padding orizzontale tablet
spacing.page-padding-x-lg      space.16       Padding orizzontale desktop
spacing.section-gap             space.16       Gap tra sezioni pagina (mobile)
spacing.section-gap-lg          space.24       Gap tra sezioni pagina (desktop)
spacing.card-padding            space.6        Padding interno card
spacing.card-padding-lg         space.8        Padding interno card large
spacing.card-gap                space.4        Gap tra elementi nella card
spacing.form-gap                space.5        Gap tra campi form
spacing.form-label-gap          space.1.5      Gap label–input
spacing.input-padding-x         space.3        Padding orizzontale input
spacing.input-padding-y         space.2.5      Padding verticale input
spacing.button-padding-x        space.4        Padding orizzontale bottone
spacing.button-padding-y        space.2.5      Padding verticale bottone
spacing.button-gap              space.2        Gap icona-testo bottone
spacing.inline-gap              space.2        Gap tra elementi inline
spacing.stack-gap               space.3        Gap tra elementi in stack
spacing.table-cell-padding-x    space.4        Padding cella tabella
spacing.table-cell-padding-y    space.3        Padding cella tabella
spacing.modal-padding           space.6        Padding interno modale
spacing.toast-padding           space.4        Padding interno toast
spacing.sidebar-padding         space.4        Padding interno sidebar
spacing.nav-item-padding-x      space.3        Padding link navigazione
spacing.nav-item-padding-y      space.2        Padding link navigazione
```

---

## 05. Design Tokens — Ombre, Raggi, Bordi

### 05.1 Ombre (Elevazione)

```
TOKEN           VALORE                                                  USO
shadow.none     none                                                    Elementi piatti
shadow.xs       0 1px 2px rgba(0,0,0,0.05)                            Separazione sottile
shadow.sm       0 1px 3px rgba(0,0,0,0.1), 0 1px 2px rgba(0,0,0,0.06) Card leggere, dropdown
shadow.md       0 4px 6px rgba(0,0,0,0.07), 0 2px 4px rgba(0,0,0,0.06) Card principali
shadow.lg       0 10px 15px rgba(0,0,0,0.1), 0 4px 6px rgba(0,0,0,0.04) Popover, dropdown estesi
shadow.xl       0 20px 25px rgba(0,0,0,0.1), 0 8px 10px rgba(0,0,0,0.04) Modal
shadow.2xl      0 25px 50px rgba(0,0,0,0.15)                           Elementi flottanti grandi
shadow.inner    inset 0 2px 4px rgba(0,0,0,0.06)                       Input incassati, well
shadow.focus    0 0 0 3px rgba(59,130,246,0.3)                         Ring di focus
shadow.error    0 0 0 3px rgba(220,38,38,0.2)                          Ring di focus errore
```

### 05.2 Raggi (Border Radius)

```
TOKEN           PX       USO
radius.none     0        Elementi sharp (tabelle, code block)
radius.xs       2        Badge piccoli
radius.sm       4        Chip, tag, badge
radius.md       6        Input, button, card compatte
radius.lg       8        Card standard, dropdown
radius.xl       12       Card grandi, modal
radius.2xl      16       Card hero, container principali
radius.3xl      24       Card molto arrotondate (stile iOS)
radius.full     9999px   Avatar, toggle, pill button, chip round
```

### 05.3 Bordi

```
TOKEN                    VALORE                      USO
border.width.default     1px                         Bordi standard
border.width.thick       2px                         Bordi enfatizzati, focus
border.width.heavy       3px                         Tab attiva, indicatore
border.style.default     solid                       Default
border.style.dashed      dashed                      Dropzone, area opzionale
border.divider           1px solid border.default     Separatore standard
border.input             1px solid border.default     Bordo input standard
border.input-focus       2px solid border.focus       Bordo input in focus
border.input-error       2px solid border.error       Bordo input in errore
```

---

## 06. Design Tokens — Movimento e Animazioni

```
DURATE
duration.instant         0ms          Nessuna animazione (stato hover immediato)
duration.micro           50ms         Feedback tattile, ripple
duration.fast            100ms        Cambio colore, opacità hover
duration.normal          200ms        Transizioni standard
duration.moderate        300ms        Apertura menu, espansione
duration.slow            400ms        Transizioni pagina, modali
duration.slower          500ms        Animazioni entrance elaborate
duration.slowest         700ms        Animazioni hero, stagger finale

EASING
easing.default           cubic-bezier(0.4, 0.0, 0.2, 1)      Standard
easing.in                cubic-bezier(0.4, 0.0, 1.0, 1.0)     Uscita dallo schermo
easing.out               cubic-bezier(0.0, 0.0, 0.2, 1.0)     Entrata nello schermo
easing.in-out            cubic-bezier(0.4, 0.0, 0.2, 1.0)     Interna allo schermo
easing.spring            cubic-bezier(0.175, 0.885, 0.32, 1.275)  Rimbalzo leggero
easing.bounce            cubic-bezier(0.68, -0.55, 0.265, 1.55)   Rimbalzo forte
easing.linear            linear                                 Progress bar, timer

TRANSIZIONI COMPOSTE
transition.color         color duration.fast easing.default
transition.opacity       opacity duration.fast easing.default
transition.transform     transform duration.normal easing.out
transition.shadow        box-shadow duration.normal easing.default
transition.expand        all duration.moderate easing.out
transition.collapse      all duration.normal easing.in
transition.page          all duration.slow easing.out
transition.modal-in      all duration.moderate easing.spring
transition.modal-out     all duration.normal easing.in
transition.fade-in       opacity duration.normal easing.out
transition.fade-out      opacity duration.fast easing.in
transition.slide-up      transform+opacity duration.moderate easing.out
transition.slide-down    transform+opacity duration.normal easing.in
transition.scale-in      transform+opacity duration.moderate easing.spring
transition.scale-out     transform+opacity duration.fast easing.in

STAGGER (per liste animate)
stagger.base             40ms         Delay incrementale tra elementi
stagger.max              8            Massimo numero di elementi con stagger
```

---

## 07. Design Tokens — Z-Index e Layering

```
TOKEN               VALORE     USO
z.hidden            -1         Elementi nascosti dietro il flusso
z.base              0          Flusso normale del documento
z.raised            1          Card elevate, elementi sovrapposti
z.dropdown          10         Dropdown menu, select
z.sticky            20         Header sticky, toolbar fisso
z.sidebar           25         Sidebar overlay mobile
z.overlay           30         Overlay scuro (backdrop modal)
z.modal             40         Finestra modale
z.popover           50         Popover, command palette
z.toast             60         Notifiche toast
z.tooltip           70         Tooltip
z.max               9999       Dev/debug overlay (mai in produzione)

REGOLA: ogni livello superiore DEVE avere un backdrop o un confine
visivo che lo separi dal contenuto sottostante.
```

---

## 08. Breakpoint e Responsive

### 08.1 Breakpoint

```
TOKEN                 PX        NOME LOGICO        TARGET
breakpoint.xs         0         mobile-portrait     Smartphone verticale
breakpoint.sm         480       mobile-landscape    Smartphone orizzontale
breakpoint.md         768       tablet              Tablet verticale
breakpoint.lg         1024      desktop-small       Desktop piccolo / tablet orizzontale
breakpoint.xl         1280      desktop             Desktop standard
breakpoint.2xl        1440      desktop-wide        Desktop largo / dashboard
breakpoint.3xl        1920      desktop-full        Full HD e oltre

REGOLA: progettare mobile-first.
Le media query usano min-width, mai max-width.
```

### 08.2 Container

```
TOKEN                      VALORE          CONTESTO
container.max.prose        680px           Testo lungo (blog, docs)
container.max.content      960px           Contenuto centrato standard
container.max.wide         1200px          Layout standard
container.max.full         1400px          Dashboard, applicazioni
container.max.fluid        100%            Sidebar layout, full-width

REGOLA: il container ha SEMPRE padding orizzontale.
Mai contenuto che tocca i bordi dello schermo.
```

---

## 09. Sistema di Griglia e Layout

### 09.1 Griglia per Breakpoint

```
BREAKPOINT    COLONNE    GUTTER     MARGINE          COMPORTAMENTO
xs (0+)       4          16px       16px             Stacking verticale
sm (480+)     4          16px       24px             Stacking, card 2-col opzionale
md (768+)     8          24px       32px             Grid a 2 colonne
lg (1024+)    12         24px       48px             Grid completa
xl (1280+)    12         24px       64px             Grid completa
2xl (1440+)   12         32px       auto (centered)  Max-width container
```

### 09.2 Pattern di Layout

```
LAYOUT TIPO              COLONNE       USO
Layout a colonna unica   12/12         Landing page, articoli, form
Layout 8+4               8 + 4         Contenuto + sidebar
Layout 4+8               4 + 8         Sidebar sinistra + contenuto
Layout 6+6               6 + 6         Confronto, split view
Layout 4+4+4             4 + 4 + 4     Card grid a 3 colonne
Layout 3+3+3+3           3 + 3 + 3 + 3 Card grid a 4 colonne
Layout sidebar+main      sidebar fissa  Dashboard standard
                         (240–280px)
                         + fluid main

DASHBOARD SPECIFICO
sidebar.width.collapsed  64px          Solo icone
sidebar.width.default    240px         Con label
sidebar.width.expanded   280px         Con sottomenu
header.height            56px          Mobile
header.height-lg         64px          Desktop
```

---

## 10. Regole Tipografiche Avanzate

```
GERARCHIA VISIVA
Solo UNO heading h1 per pagina.
Sequenza heading: h1 → h2 → h3 → h4. Mai saltare livelli.
Massimo 3 livelli di heading per sezione.

LARGHEZZA DEL PARAGRAFO
Massima larghezza testo: 65–75 caratteri (container.max.prose).
Oltre i 75 caratteri la leggibilità degrada.
In dashboard con colonne strette: minimo 35 caratteri.

CONTRASTO TIPOGRAFICO
Usare massimo 2 font family per progetto (display + body).
Usare massimo 3 pesi per pagina.
Il contrasto tra heading e body deve essere evidente:
  heading = semibold/bold + size maggiore
  body = regular + size base

TESTO SU BOTTONI
Sempre in sentence case ("Salva modifiche"), mai tutto MAIUSCOLO.
Eccezione: overline e label di stato.
Lunghezza massima CTA: 3–4 parole.

TESTO TRONCATO
Usare text-overflow: ellipsis con max-width e white-space: nowrap.
Mai troncare heading principali.
Nei tooltip mostrare il testo completo quando troncato.
Nelle tabelle: troncare dopo 2 righe massimo con line-clamp.

NUMERI
Usare font-variant-numeric: tabular-nums nelle tabelle e dashboard.
Allineare i numeri a destra nelle colonne tabellari.
Usare separatore delle migliaia secondo la locale:
  IT: 1.234.567,89
  EN: 1,234,567.89
  DE: 1.234.567,89
```

---

## 11. Internazionalizzazione (i18n) e Multilingua

```
REGOLE CRITICHE

01. MAI dimensionare un componente sulla lunghezza di una singola lingua.
    "Save" in inglese = "Speichern" in tedesco = "Enregistrer" in francese.
    Prevedere +40% di espansione del testo rispetto all'inglese.

02. Mai usare flag nazionali come selettore di lingua.
    Una bandiera rappresenta un paese, non una lingua.
    Usare: nome della lingua nella lingua stessa ("Italiano", "English", "Deutsch").

03. Layout RTL (arabo, ebraico):
    - Invertire orizzontalmente tutto il layout (margini, padding, icone direzionali).
    - Le icone non direzionali NON si invertono (search, home, settings).
    - Le icone direzionali SI invertono (arrow-left, reply, undo).
    - I numeri restano LTR anche in contesto RTL.

04. Date e orari secondo la locale:
    IT:  23/04/2026    14:30
    EN:  04/23/2026    2:30 PM
    DE:  23.04.2026    14:30
    JP:  2026/04/23    14:30
    Usare sempre l'API Intl.DateTimeFormat o equivalente.

05. Valute secondo la locale:
    IT:  1.234,56 €
    EN:  $1,234.56
    DE:  1.234,56 €
    JP:  ¥1,234

06. Pluralizzazione:
    Non usare mai "1 item(s)".
    Usare regole di pluralizzazione per lingua:
      IT: "1 elemento" / "2 elementi"
      EN: "1 item" / "2 items"
      Alcune lingue hanno più forme plurali (es. russo: 3 forme).

07. Non concatenare stringhe per costruire frasi.
    SBAGLIATO: "Hai " + count + " messaggi nuovi"
    CORRETTO:  usare template con sostituzione: "Hai {count} messaggi nuovi"

08. Prevedere nei componenti:
    - Testo che va a capo su 2+ righe
    - Label molto corte (cinese: 2 caratteri) e molto lunghe (tedesco: 30+ caratteri)
    - Caratteri con ascendenti/discendenti diversi (ÅÖÜ, ğş, กข)

09. Font fallback:
    Avere sempre un fallback font che copra i caratteri mancanti.
    system-ui copre la maggior parte dei set ma non è stilisticamente coerente.
    Per supporto CJK: includere Noto Sans come fallback esplicito.

10. Testare SEMPRE il prototipo con almeno:
    - Italiano (lingua base)
    - Inglese (lingua internazionale)
    - Tedesco (lingua con parole lunghe, stress test)
    - Se possibile: arabo (RTL)
```

---

## 12. Inventario Componenti

```
CATEGORIA        COMPONENTE              VARIANTI MINIME
─────────────────────────────────────────────────────────────────────────
INPUT            Button                  primary, secondary, ghost, outline, destructive,
                                         link | sizes: xs, sm, md, lg
                 IconButton              sizes: sm, md, lg | variant: default, ghost
                 TextField               default, error, success, disabled | with label,
                                         helper, prefix/suffix, clearable
                 TextArea                default, error | resizable, autosize
                 Select                  native, custom | searchable, multi-select
                 Checkbox                unchecked, checked, indeterminate, disabled
                 Radio                   default, disabled | RadioGroup
                 Toggle / Switch         on, off, disabled | with label
                 Slider                  single, range | with value label
                 DatePicker              single date, date range
                 TimePicker              12h, 24h
                 FileUpload              dropzone, button | with preview
                 SearchField             with clear, with suggestions
                 ColorPicker             preset, custom
                 Rating                  stars, numeric (1–5, 1–10)

NAVIGAZIONE      Navbar                  desktop, mobile (hamburger) | with search,
                                         avatar, notifications
                 Sidebar                 expanded, collapsed, mobile-overlay
                 Tabs                    underline, pill, boxed | with icon, with badge
                 Breadcrumb              standard, truncated
                 Pagination              numbered, prev/next, load-more, infinite scroll
                 Link                    inline, standalone, nav-item
                 Stepper                 horizontal, vertical | with status
                 BottomNav               mobile only | 3–5 items

DATI             Table                   default, compact, striped | sortable, selectable,
                                         expandable, with pagination
                 DataGrid                virtual scroll, resizable columns, inline edit
                 Card                    default, interactive (clickable), compact, horizontal
                 Avatar                  sizes: xs, sm, md, lg, xl | with status indicator,
                                         with fallback initials
                 Badge                   neutral, brand, success, warning, error, info |
                                         dot, count, label
                 Tag / Chip              default, removable, selectable, with avatar
                 Stat / KPI              number, delta/change, with sparkline
                 List                    simple, with icon, with avatar, with action
                 Timeline                vertical, horizontal | with connector
                 EmptyState              with illustration, title, description, CTA

FEEDBACK         Toast / Snackbar        success, error, warning, info | with action,
                                         dismissable, with progress
                 Alert / Banner          same variants | inline, dismissable
                 Dialog / Modal          sizes: sm, md, lg, fullscreen | with form,
                                         confirmation, destructive
                 Drawer                  left, right, bottom | sizes: sm, md, lg
                 Tooltip                 top, right, bottom, left | with rich content
                 Popover                 click-triggered, hover-triggered
                 ProgressBar             determinate, indeterminate, with label
                 Spinner / Loader        sizes: sm, md, lg | inline, overlay
                 Skeleton                text, circular, rectangular | animate

OVERLAY          DropdownMenu            with icons, with keyboard shortcuts, nested
                 CommandPalette          searchable, with categories
                 ContextMenu             right-click triggered

LAYOUT           Container               prose, content, wide, full
                 Section                 with heading, with divider
                 Grid                    responsive auto-fill
                 Stack                   horizontal, vertical | with gap
                 Divider                 horizontal, vertical | with label
                 Accordion / Collapse    single, multi | with icon
                 AspectRatio             16:9, 4:3, 1:1, custom

MEDIA            Image                   with fallback, with lightbox, with lazy load
                 Video                   with controls, with poster
                 Carousel                with dots, with arrows, auto-play
                 Gallery                 grid, masonry
```

---

## 13. Stati dei Componenti

```
OGNI componente interattivo DEVE avere TUTTI questi stati:

STATO            VISUALE                           NOTE
default          Aspetto base                      Stato iniziale
hover            Cambiamento colore/ombra sottile   Solo desktop (niente hover su touch)
active           Leggera pressione (scale o darker) Feedback pressione
focus-visible    Ring di focus visibile              Solo tastiera, non mouse
disabled         Opacità ridotta (0.5) + no cursor   pointer-events: none
loading          Spinner o skeleton                  Disabilitare interazione
error            Bordo rosso + messaggio errore      Accessibile: aria-invalid
success          Bordo verde + conferma              Temporaneo o persistente
selected         Background highlight                Per toggle, chip, radio, checkbox
dragging         Elevazione + opacità ridotta        Per drag & drop

REGOLE
- Mai usare solo il colore per indicare lo stato (accessibilità).
- Lo stato disabled MAI su un CTA principale senza spiegazione del perché.
- Loading state: sempre un timeout massimo con fallback errore.
- Focus ring: DEVE essere visibile su QUALUNQUE sfondo (testare su chiaro e scuro).
```

---

## 14. Proprietà dei Componenti

```
PROPRIETÀ FIGMA / STITCH / CLAUDE DESIGN

Variant Properties     (mutualmente esclusive)
  size:                xs, sm, md, lg, xl
  variant:             primary, secondary, ghost, outline, destructive
  state:               default, hover, active, focus, disabled, loading, error

Boolean Properties     (toggle on/off)
  showIcon:            true / false
  showBadge:           true / false
  showDescription:     true / false
  showAvatar:          true / false
  showHelper:          true / false
  showClear:           true / false
  isRequired:          true / false
  isFullWidth:         true / false

Text Properties        (contenuto editabile)
  label:               "Testo bottone"
  description:         "Testo descrittivo opzionale"
  placeholder:         "Inserisci valore..."
  helperText:          "Testo di aiuto sotto l'input"
  errorText:           "Messaggio di errore"
  badgeText:           "99+"

Instance Swap          (componente intercambiabile)
  leadingIcon:         qualsiasi icona
  trailingIcon:        qualsiasi icona
  avatar:              componente Avatar
  statusIndicator:     componente Badge/Dot

REGOLA: mai usare layer nascosti per simulare varianti.
Usare SEMPRE le proprietà native del tool di prototipazione.
```

---

## 15. Pattern di Navigazione

```
TIPO                 QUANDO                              REGOLE

Top Navbar           Siti web, landing page,              Max 7 voci visibili.
                     web app semplici                     Oltre: usare menu "Altro" o mega-menu.
                                                          Mobile: hamburger menu.
                                                          Logo sempre a sinistra (LTR) / destra (RTL).
                                                          CTA primario a destra.

Sidebar              Dashboard, applicazioni              Collapse a 64px (solo icone) su schermi < lg.
                     complesse, admin panel               Tooltip sulle icone quando collapsed.
                                                          Sezione attiva: background highlight.
                                                          Scrollabile se il menu è lungo.
                                                          Raggruppare voci con divider + label sezione.

Bottom Tab Bar       App mobile, PWA                      Max 5 voci. Oltre: usare "Altro".
                                                          Icona + label SEMPRE (no icona sola).
                                                          Voce attiva: colore brand + peso bold.
                                                          Altezza: 56px (con safe area su iOS).

Breadcrumb           Gerarchie profonde                   Non usare come unica navigazione.
                     (e-commerce, docs, CMS)              Max 4 livelli visibili, troncare i centrali.
                                                          L'ultimo elemento NON è un link.

Tabs                 Sezioni dello stesso contenuto        Max 6 tabs visibili. Oltre: scroll orizzontale.
                                                          Mai usare per navigazione tra pagine diverse.
                                                          Tab attiva: indicatore visivo evidente.

Stepper              Flussi multi-step (checkout,          Max 5 step. Oltre: raggruppare in fasi.
                     onboarding, wizard)                   Step completati: check verde.
                                                          Step corrente: evidenziato.
                                                          Permettere navigazione indietro.
```

---

## 16. Pattern per Dashboard

```
STRUTTURA BASE

┌──────────────────────────────────────────────────────────┐
│  Header (64px) — logo, search, notifications, avatar    │
├─────────┬────────────────────────────────────────────────┤
│         │                                                │
│ Sidebar │  Page Header (titolo + azioni + breadcrumb)    │
│ (240px) │                                                │
│         │  KPI Row (4 stat card)                         │
│         │                                                │
│         │  Chart Area (1 o 2 grafici)                    │
│         │                                                │
│         │  Table / List (contenuto principale)           │
│         │                                                │
│         │  Pagination                                    │
│         │                                                │
└─────────┴────────────────────────────────────────────────┘

KPI CARD
  Struttura: label (overline) + numero grande (stat-xl) + delta (badge con freccia)
  Minimo: label + valore
  Opzionale: sparkline, icona, periodo di confronto
  Grid: 4 colonne su desktop, 2 su tablet, 1 su mobile

CHART AREA
  Titolo del grafico: heading-4
  Legenda: sotto o a destra del grafico
  Tooltip interattivo su hover
  Responsive: semplificare su mobile (nascondere griglia, ridurre punti)
  Colori grafici: usare la scala brand + accent, mai colori casuali

TABLE
  Header: sticky in scroll verticale
  Righe alternate: surface.subtle ogni 2 righe (opzionale)
  Azioni riga: icone a destra, visibili su hover (desktop) o sempre (mobile)
  Selezione: checkbox a sinistra
  Sorting: icona freccia nel header
  Filtri: sopra la tabella, inline o in pannello laterale
  Empty state: illustrazione + testo + CTA

FILTRI DASHBOARD
  Posizione: sopra il contenuto, sotto il page header
  Tipo: chip selezionabili, dropdown, date range
  Persistenza: i filtri attivi devono essere sempre visibili
  Reset: bottone "Cancella filtri" sempre presente quando attivi
```

---

## 17. Pattern per Form e Input

```
STRUTTURA CAMPO

Label (obbligatorio, mai solo placeholder)       text.label-base
┌─────────────────────────────────────────┐
│ [icona] Placeholder...           [azione]│      Input
└─────────────────────────────────────────┘
Helper text o messaggio errore                   text.caption

REGOLE

01. Label SOPRA l'input, mai a sinistra (eccezione: form inline compatti).
02. Placeholder: suggerimento di formato, MAI sostituto della label.
03. Campo obbligatorio: asterisco rosso (*) accanto alla label.
    Alternativa: indicare "(opzionale)" sui campi non obbligatori.
04. Validazione:
    - Inline (tempo reale) per formato (email, telefono).
    - On blur per controlli semplici.
    - On submit per validazione server.
    - Messaggio errore: specifico ("Inserisci un'email valida"), mai generico ("Campo non valido").
05. Errore: bordo rosso + icona errore + messaggio sotto il campo.
    Il messaggio errore SOSTITUISCE l'helper text, non si aggiunge.
06. Successo: bordo verde + check (solo se utile, es. username disponibile).
07. Gruppi logici: raggruppare con fieldset e legend. Separare con divider.
08. Azioni form:
    - CTA primario a destra (LTR) o a sinistra (RTL).
    - "Annulla" è sempre secondario o ghost.
    - In form modali: azioni nel footer del modale.
09. Form multi-step:
    - Stepper in alto.
    - Salvare progresso tra step.
    - Permettere navigazione indietro senza perdere dati.
10. Autofill: supportare autocomplete del browser (name, email, tel, address).
```

---

## 18. Pattern per Tabelle e Dati

```
HEADER
  Background: surface.subtle
  Testo: text.label-base, uppercase opzionale, colore text.secondary
  Sorting: icona freccia, toggle asc/desc al click
  Resize colonne: opzionale, con handle visibile su hover

RIGHE
  Altezza minima: 48px (compact) / 56px (default) / 64px (comfortable)
  Hover: background surface.subtle
  Selected: background brand.50 + checkbox checked
  Bordo inferiore: border.subtle

CELLE
  Allineamento testo: sinistra
  Allineamento numeri: destra
  Allineamento azioni: centro o destra
  Troncamento: ellipsis dopo 2 righe (line-clamp: 2)
  Tooltip: mostrare testo completo su hover se troncato

PAGINAZIONE
  Posizione: sotto la tabella, allineata a destra
  Mostrare: "Risultati 1–20 di 456"
  Opzioni per pagina: 10, 20, 50 (dropdown)
  Navigazione: prev/next + numeri pagina (max 5 visibili)

RESPONSIVE
  < md: convertire tabella in card list o nascondere colonne secondarie
  Colonne prioritarie: quelle che identificano la riga (nome, ID)
  Colonne secondarie: nascondere su mobile, mostrare in espansione riga
  
EMPTY STATE
  Nessun dato: illustrazione + "Nessun risultato trovato" + suggerimento
  Nessun dato con filtri attivi: "Nessun risultato per questi filtri" + "Cancella filtri"
  Errore caricamento: "Si è verificato un errore" + "Riprova"
```

---

## 19. Pattern per Feedback e Notifiche

```
TOAST / SNACKBAR
  Posizione: bottom-right (desktop), bottom-center (mobile)
  Durata: 5 secondi default, con pausa su hover
  Dismissable: icona X o swipe (mobile)
  Max visibili: 3 stacked (il più recente in basso)
  Azione opzionale: un solo bottone ghost ("Annulla", "Vedi")
  Mai usare per errori critici (usare Alert inline o Dialog)

ALERT / BANNER
  Posizione: inline, sotto il page header o sopra il contenuto correlato
  Dismissable: solo se non critico
  Non dismissable: errori di sistema, avvisi legali
  Struttura: icona + titolo (opzionale) + messaggio + azione (opzionale)

DIALOG / MODAL
  Conferma: "Sei sicuro?" + descrizione conseguenza + 2 azioni
  Distruttivo: CTA rosso "Elimina" + secondario "Annulla"
  Informativo: singolo CTA "Ho capito"
  Con form: validazione prima della chiusura
  Chiusura: click backdrop + tasto Esc + pulsante X
  Focus trap: il focus resta dentro il modale (accessibilità)
  Backdrop: surface.inverse con opacity 0.5

SKELETON
  Usare per ogni contenuto in caricamento (mai schermata bianca vuota)
  Forma: rettangoli arrotondati che replicano la struttura del contenuto
  Animazione: shimmer da sinistra a destra (gradient animato)
  Durata: massimo 3 secondi, poi fallback a spinner se ancora in caricamento

PROGRESS
  Determinato: progress bar con percentuale (upload, download, step)
  Indeterminato: spinner o progress bar infinita (caricamento generico)
  Long task: progress con stima tempo + possibilità di annullare
```

---

## 20. Pattern per Contenuti e Card

```
CARD STANDARD
  Struttura: [immagine] + heading + body + [meta] + [azioni]
  Padding: spacing.card-padding (space.6)
  Raggio: radius.lg
  Ombra: shadow.sm (default) / shadow.md (hover se interattiva)
  Click: se la card è cliccabile, TUTTA la card è cliccabile (no solo il titolo)
  Hover: leggero lift (translateY -2px + shadow.md)
  Focus: focus ring sull'intera card
  Responsive: da grid a stack verticale sotto breakpoint.md

CARD HERO
  Come card standard ma:
  - Immagine grande (aspect ratio 16:9 o 3:2)
  - Heading: text.heading-2
  - Può occupare 2 colonne del grid

CARD KPI
  Struttura: label (overline) + valore (stat-xl) + delta (badge)
  Background: surface.default con border o surface.subtle senza border
  Non cliccabile di default (se cliccabile: aggiungere icona freccia)

CARD LIST (mobile)
  Usata al posto di tabelle su mobile
  Struttura: avatar/icona + titolo + sottotitolo + valore a destra
  Altezza: 72–80px
  Separatore: border.subtle tra card
  Swipe action: opzionale (archivia, elimina)

CONTENUTO LUNGO
  Prose: max-width container.max.prose (680px)
  Immagini inline: max-width 100% del container, con caption sotto
  Code block: sfondo surface.inset, font mono, con copia-incolla
  Blockquote: bordo sinistro brand.500 (4px) + padding + testo italic
  Lista: bullet personalizzato o numero, gap space.2 tra item
```

---

## 21. Iconografia

```
LIBRERIA CONSIGLIATA
  Lucide Icons (open source, coerente, buon supporto)
  Alternativa: Phosphor Icons, Heroicons

DIMENSIONI
  icon.size.xs       12px     Badge, inline tiny
  icon.size.sm       16px     Inline con testo sm, badge
  icon.size.md       20px     Default, con testo base
  icon.size.lg       24px     Bottoni, navigazione
  icon.size.xl       32px     Heading con icona, empty state
  icon.size.2xl      48px     Empty state, illustrazioni minime

STILE
  Stroke width: 1.5px (default Lucide) — MAI mischiare filled e outlined.
  Scegliere UNO stile e mantenerlo ovunque.
  Colore: ereditato dal testo (currentColor) di default.

REGOLE
  - Icona + testo: gap space.2 (8px)
  - Icona senza testo: DEVE avere aria-label o title per accessibilità
  - Icone decorative: aria-hidden="true"
  - Icone interattive: minimo touch target 44x44px (anche se l'icona è 20px)
  - Mai icone sole come unico elemento di navigazione (sempre con label)
    Eccezione: sidebar collapsed (con tooltip obbligatorio)
  - Icone direzionali: invertire in RTL (arrow-left, chevron-right, reply)
  - Icone non direzionali: NON invertire in RTL (search, home, settings, star)
```

---

## 22. Immagini e Media

```
ASPECT RATIO
  ratio.hero         16:9        Hero image, video cover
  ratio.card         3:2         Card immagine standard
  ratio.square       1:1         Avatar, thumbnail, gallery
  ratio.portrait     2:3         Card prodotto, profilo
  ratio.wide         21:9        Banner ultra-wide

CARICAMENTO
  Lazy loading: tutte le immagini sotto il fold (loading="lazy")
  Placeholder: skeleton shimmer o dominant color blur
  Fallback: immagine placeholder generica se errore di caricamento
  Formato: WebP con fallback JPG/PNG

RESPONSIVE
  Servire immagini a dimensione adeguata per breakpoint (srcset)
  Mobile: immagini max 750px di larghezza
  Desktop: immagini max 1920px di larghezza
  Retina: servire @2x per schermi HiDPI

AVATAR
  Fallback: iniziali (prima lettera nome + cognome) su background generato
  Generazione colore background: hash del nome per coerenza
  Border: 2px solid surface.default quando sovrapposti (avatar group)
  Status indicator: dot in basso a destra (online=verde, offline=grigio, busy=rosso)
```

---

## 23. Accessibilità (WCAG 2.2 AA)

```
CONTRASTO COLORE
  Testo normale (< 18px regular / < 14px bold):    minimo 4.5:1
  Testo grande (>= 18px regular / >= 14px bold):    minimo 3:1
  Componenti UI e icone significative:              minimo 3:1
  Elementi decorativi e disabled:                   nessun requisito

  TESTARE: usare plugin (Stark, Color Contrast Checker, axe)
  TESTARE: su sfondo chiaro E scuro

FOCUS
  Ogni elemento interattivo DEVE avere un focus visibile.
  Focus ring: 2px solid color.border.focus + 2px offset.
  Mai outline: none o outline: 0 senza sostituzione.
  Ordine di focus (tab order): logico, da sinistra a destra (LTR), dall'alto al basso.
  Skip link: primo elemento focusabile, "Vai al contenuto principale".

TARGET DIMENSIONE (WCAG 2.2 - 2.5.8)
  Minimo touch target:         44 × 44px
  Minimo click target:         24 × 24px (con 44px di spacing tra target adiacenti)
  Spacing tra target adiacenti: minimo 8px

ARIA
  Landmark: header, nav, main, aside, footer con ruoli ARIA appropriati.
  Form: ogni input ha una label associata (for/id o aria-labelledby).
  Errori: aria-invalid="true" + aria-describedby collegato al messaggio errore.
  Live region: aria-live="polite" per toast e aggiornamenti non urgenti.
  Live region: aria-live="assertive" per errori critici.
  Modal: aria-modal="true" + focus trap + chiusura con Esc.
  Stato loading: aria-busy="true" durante caricamento.

NAVIGAZIONE DA TASTIERA
  Tab:          avanza al prossimo elemento focusabile
  Shift+Tab:    torna all'elemento precedente
  Enter/Space:  attiva bottoni e link
  Arrow keys:   naviga dentro gruppi (tabs, menu, radio group)
  Esc:          chiude overlay (modal, dropdown, popover)
  Home/End:     primo/ultimo elemento di una lista

CONTENUTI
  Heading: sequenza h1→h2→h3, mai saltare livelli
  Immagini: alt text descrittivo o alt="" se decorativa
  Link: testo del link auto-esplicativo ("Leggi l'articolo", mai "Clicca qui")
  Tabelle: header di colonna con <th scope="col">
  Colore: mai il solo indicatore di stato (aggiungere icona o testo)
  Animazioni: rispettare prefers-reduced-motion: reduce
  Testo: mai tutto maiuscolo per frasi intere (solo label brevi o overline)

SCREEN READER
  Testare con VoiceOver (macOS/iOS) o NVDA (Windows).
  Ogni interazione deve essere comprensibile senza visuale.
  Icone decorative: aria-hidden="true".
  Icone significative: aria-label="Descrizione".
```

---

## 24. Dark Mode

### 24.1 Token Override

```
SUPERFICI (dark)
surface.page              gray.950
surface.default           gray.900
surface.subtle            gray.800
surface.muted             gray.700
surface.inset             gray.800
surface.raised            gray.800
surface.overlay           gray.800
surface.inverse           gray.50
surface.brand             brand.400
surface.brand-subtle      brand.950 con opacity 0.5

TESTO (dark)
text.primary              gray.50
text.secondary            gray.400
text.tertiary             gray.500
text.disabled             gray.600
text.inverse              gray.900
text.brand                brand.300
text.success              #4ADE80
text.warning              #FACC15
text.error                #FCA5A5
text.info                 #93C5FD

BORDI (dark)
border.default            gray.700
border.strong             gray.600
border.subtle             gray.800
border.focus              brand.400
border.error              #F87171
border.success            #4ADE80

ICONE (dark)
icon.default              gray.400
icon.strong               gray.300
icon.subtle               gray.500
icon.disabled             gray.600
icon.brand                brand.300
icon.inverse              gray.900

OMBRE (dark)
  Le ombre in dark mode usano opacità maggiore:
  shadow.sm     0 1px 3px rgba(0,0,0,0.4), 0 1px 2px rgba(0,0,0,0.3)
  shadow.md     0 4px 6px rgba(0,0,0,0.4), 0 2px 4px rgba(0,0,0,0.3)
  shadow.lg     0 10px 15px rgba(0,0,0,0.5), 0 4px 6px rgba(0,0,0,0.3)
  
  In dark mode i bordi sono spesso più efficaci delle ombre
  per separare gli elementi. Preferire border a shadow quando possibile.
```

### 24.2 Regole Dark Mode

```
01. Mai invertire semplicemente i colori. Il dark mode ha una sua logica.
02. Le superfici più elevate sono PIÙ CHIARE in dark mode (gray.800 > gray.900).
    È il contrario del light mode dove l'elevazione = ombra.
03. Il testo bianco puro (#FFFFFF) è troppo aggressivo. Usare gray.50 (#F9FAFB).
04. I colori brand/accent vanno desaturati leggermente in dark mode.
05. Le immagini possono necessitare di un overlay scuro o riduzione di luminosità.
06. Rispettare prefers-color-scheme: dark per il cambio automatico.
07. Offrire SEMPRE un toggle manuale (non solo automatico).
08. Testare TUTTI i componenti in entrambi i temi prima del rilascio.
09. Le illustrazioni e gli SVG devono avere varianti light/dark.
10. In Figma/Stitch: usare variable modes, mai duplicare componenti.
```

---

## 25. Prototipazione — Regole Generali

```
01. DATI REALISTICI
    Mai lorem ipsum in prototipi presentati a stakeholder.
    Usare nomi reali (o realistici), numeri verosimili, date attuali.
    Testare con:
    - Stringhe corte: "OK", "Sì"
    - Stringhe lunghe: "Conferma la modifica delle impostazioni di sicurezza"
    - Numeri grandi: 1.234.567,89
    - Nomi lunghi: "Maria Giovanna Della Franceschina"
    - Testo in 2+ lingue: italiano + inglese minimo

02. OGNI SCHERMATA HA UN OBIETTIVO
    Prima di progettare uno schermo, rispondere:
    "Cosa deve fare l'utente qui?"
    Se la risposta non è chiara, lo schermo non dovrebbe esistere.

03. NESSUN VICOLO CIECO
    Ogni schermata deve avere:
    - Un modo per tornare indietro
    - Un'azione primaria chiara
    - Uno stato alternativo (empty, error, loading)

04. STATI OBBLIGATORI PER OGNI VISTA
    - Default (con dati)
    - Empty (nessun dato)
    - Loading (skeleton o spinner)
    - Error (errore di caricamento)
    - Partial (pochi dati, verifica che il layout regga)

05. ANNOTAZIONI
    Ogni flusso prototipale deve avere note che spiegano:
    - Comportamento di interazione non ovvio
    - Logica condizionale ("se utente non autenticato → redirect login")
    - Requisiti di animazione
    - Edge case gestiti
```

---

## 26. Prototipazione — Flussi e Struttura

### 26.1 Struttura Pagine Progetto

```
PAGINA                  CONTENUTO
─────────────────────────────────────────────────────────────
🎨 Design System        Token, stili, componenti base
📐 Wireframe             Struttura low-fidelity
🖥 Desktop               Schermate desktop hi-fi
📱 Mobile                Schermate mobile hi-fi
📊 Dashboard             Schermate dashboard specifiche
▶️ Flussi Prototipo      Flussi connessi con interazioni
🌍 i18n Test             Schermate con contenuti multilingua
🌙 Dark Mode             Varianti dark mode (se non gestite con variable)
🧪 Playground            Esperimenti e test
📦 Archivio              Versioni precedenti
📋 Handoff Notes         Specifiche per sviluppatori
```

### 26.2 Naming Frame

```
FORMATO: [numero]-[sezione]-[stato]-[variante]

ESEMPI:
  01-onboarding-welcome-default
  01-onboarding-welcome-loading
  02-login-form-default
  02-login-form-error
  02-login-form-loading
  03-dashboard-overview-default
  03-dashboard-overview-empty
  03-dashboard-overview-filtered
  04-settings-profile-default
  04-settings-profile-editing
  05-modal-confirm-delete
  05-modal-success-feedback
```

### 26.3 Cover Frame per Flusso

```
Ogni flusso prototipale inizia con un frame di copertura:

┌─────────────────────────────────────────────┐
│                                             │
│  NOME FLUSSO                                │
│  es. "Registrazione Utente — Email"         │
│                                             │
│  OBIETTIVO                                  │
│  es. "L'utente crea un account e           │
│       completa il profilo base"             │
│                                             │
│  ENTRY POINT:    01-onboarding-welcome      │
│  EXIT POINT:     03-dashboard-overview      │
│                                             │
│  STEP HAPPY PATH:                           │
│    1. Welcome screen                        │
│    2. Inserimento email                     │
│    3. Verifica email                        │
│    4. Creazione password                    │
│    5. Profilo base                          │
│    6. Dashboard                             │
│                                             │
│  EDGE CASE:                                 │
│    - Email già registrata → errore inline   │
│    - Password debole → validazione inline   │
│    - Timeout verifica → bottone "Reinvia"   │
│                                             │
│  DESIGNER:    [Nome]                        │
│  ULTIMO AGG:  [Data]                        │
│  VERSIONE:    [v1.2]                        │
│                                             │
└─────────────────────────────────────────────┘
```

---

## 27. Prototipazione — Interazioni e Transizioni

```
TRANSIZIONI TRA SCHERMATE
  Navigazione avanti:     Slide da destra     duration.moderate  easing.out
  Navigazione indietro:   Slide da sinistra   duration.moderate  easing.out
  Tab switch:             Dissolve            duration.normal    easing.default
  Nuova sezione:          Dissolve            duration.slow      easing.default

OVERLAY
  Modal apertura:         Scale da 0.95 a 1   duration.moderate  easing.spring
                          + fade backdrop
  Modal chiusura:         Scale da 1 a 0.95   duration.normal    easing.in
                          + fade backdrop
  Drawer apertura:        Slide dal lato       duration.moderate  easing.out
  Drawer chiusura:        Slide verso il lato  duration.normal    easing.in
  Dropdown apertura:      Scale Y da 0.95      duration.fast      easing.out
                          + fade
  Dropdown chiusura:      Fade                 duration.fast      easing.in
  Toast entrata:          Slide up + fade      duration.moderate  easing.spring
  Toast uscita:           Fade                 duration.normal    easing.in
  Tooltip:                Fade                 duration.fast      easing.default
                          delay: 200ms (apertura), 0ms (chiusura)

MICRO-INTERAZIONI
  Button hover:           Cambia colore        duration.fast      easing.default
  Button press:           Scale 0.97           duration.micro     easing.default
  Card hover:             TranslateY -2px      duration.normal    easing.out
                          + shadow.md
  Toggle switch:          Slide knob           duration.normal    easing.spring
  Checkbox:               Scale + fill         duration.fast      easing.spring
  Accordion expand:       Height auto          duration.moderate  easing.out
  Accordion collapse:     Height 0             duration.normal    easing.in

SCROLL
  Header sticky:          Ombra appare dopo scroll > 0
  Scroll-to-top:          Bottone appare dopo scroll > 300px
  Parallax:               SOLO se prefers-reduced-motion non è "reduce"
  Infinite scroll:        Spinner/skeleton in fondo alla lista
  Pull-to-refresh:        Solo mobile, spinner sopra il contenuto
```

---

## 28. Prototipazione — Stitch Specifico

```
REGOLE PER STITCH

01. STRUTTURA COMPONENTI
    Usare la struttura nativa di Stitch per i componenti:
    - Variants: definire come proprietà del componente
    - Slots: usare slot per contenuto intercambiabile
    - Props: esporre le proprietà necessarie al design system

02. RESPONSIVE IN STITCH
    Configurare i breakpoint nel progetto:
    - Mobile: 375px (iPhone standard)
    - Tablet: 768px
    - Desktop: 1440px
    Usare il sistema di responsive nativo di Stitch per ogni frame.

03. INTERAZIONI
    Usare le interazioni native di Stitch:
    - Click → Navigate: per cambio pagina
    - Click → Open overlay: per modal/drawer
    - Hover → Change variant: per stati hover
    - Scroll → Animate: per animazioni scroll-triggered
    Definire le transizioni secondo i token del capitolo 06.

04. VARIABILI
    Mappare TUTTI i token del design system come variabili Stitch:
    - Color variables per ogni token semantico
    - Spacing variables per la scala spaziatura
    - Typography variables per gli stili composti
    Usare la funzione di variable modes per light/dark.

05. AUTO-LAYOUT
    SEMPRE usare auto-layout per i container.
    Mai posizionamento assoluto tranne che per:
    - Badge/dot di notifica su avatar
    - Indicatore di stato
    - Elementi decorativi sovrapposti

06. ASSET MANAGEMENT
    Icone: importare come componenti, non come immagini.
    Illustrazioni: importare come SVG quando possibile.
    Immagini: usare placeholder realistici (Unsplash integration).

07. HANDOFF
    Usare le funzionalità di inspect di Stitch per:
    - Esportare CSS/token
    - Misurare distanze
    - Verificare allineamento alla griglia
    Aggiungere annotazioni con il tool di commento nativo.
```

---

## 29. Prototipazione — Claude Design Specifico

```
REGOLE PER CLAUDE DESIGN

01. ISTRUZIONI CHIARE NEL PROMPT
    Quando si genera un componente o una pagina, includere nel prompt:
    - Tipo di componente
    - Varianti richieste
    - Contesto d'uso (sito, dashboard, mobile app)
    - Token da applicare (riferimento a questo DESIGN.md)
    - Lingua del contenuto
    - Tema (light / dark)

02. CODICE GENERATO
    Il codice deve:
    - Usare CSS custom properties per TUTTI i token
    - Usare semantic class names (mai classi generate)
    - Essere responsive con breakpoint definiti
    - Includere stati hover, focus, disabled
    - Includere attributi ARIA appropriati
    - Essere compatibile con il framework target (React, HTML, Vue)

03. STRUTTURA CSS VARIABLES
    Generare un blocco :root con tutti i token:

    :root {
      /* Colors - Surfaces */
      --surface-page: #FFFFFF;
      --surface-default: #FFFFFF;
      --surface-subtle: #F9FAFB;
      /* ... tutti i token semantici */
      
      /* Typography */
      --font-display: "Plus Jakarta Sans", sans-serif;
      --font-body: "DM Sans", sans-serif;
      --font-mono: "JetBrains Mono", monospace;
      /* ... */
      
      /* Spacing */
      --space-1: 4px;
      --space-2: 8px;
      /* ... */
    }

    [data-theme="dark"] {
      --surface-page: #030712;
      --surface-default: #111827;
      /* ... override dark mode */
    }

04. OUTPUT ATTESO
    Ogni generazione Claude Design deve produrre:
    - Codice funzionante (non snippet parziali)
    - Tutti gli stati del componente
    - Responsive behavior
    - Dark mode support (se richiesto)
    - Commenti nel codice per handoff

05. QUALITÀ
    Il codice generato deve:
    - Passare validazione HTML (W3C)
    - Avere contrasto AA verificabile
    - Non usare !important
    - Non usare inline styles (tranne CSS-in-JS)
    - Usare unità rem per dimensioni testo
    - Usare unità px per spaziatura e dimensioni fisse
    - Usare clamp() per dimensioni responsive

06. ITERAZIONE
    Quando si itera su un componente:
    - Riferirsi al nome del componente e alla variante
    - Specificare solo ciò che cambia
    - Mantenere coerenza con le generazioni precedenti
    - Non rigenerare da zero se basta una modifica

07. INTEGRAZIONE CON STITCH
    Il codice generato da Claude Design deve essere:
    - Importabile in Stitch come componente web
    - Compatibile con il sistema di variabili Stitch
    - Strutturato in modo da poter essere convertito in componente Stitch
    - Documentato con le proprietà esposte
```

---

## 30. Naming Convention

```
LIVELLO            FORMATO              ESEMPIO
─────────────────────────────────────────────────────────────
Token              kebab-case           surface-page, text-primary
Componente Figma   PascalCase           Button, TextField, NavSidebar
Variante Figma     PascalCase           Primary-Default, Ghost-Hover
Layer Figma        kebab-case           card-header, nav-logo, hero-cta
Frame Figma        kebab-num            01-dashboard-overview-default
Pagina Figma       emoji + Nome         🖥 Desktop
Classe CSS         kebab-case           .btn-primary, .card-header
Variabile CSS      --kebab-case         --color-brand-500, --space-4
Componente React   PascalCase           <Button>, <TextField>
Prop React         camelCase            isDisabled, showIcon, onClick
File               kebab-case           button.tsx, design-tokens.css
Cartella           kebab-case           components/, design-system/
Icona              kebab-case           arrow-right, chevron-down

REGOLE
  - Mai nomi generici: "Frame 1", "Group 5", "Rectangle 12"
  - Mai abbreviazioni non standard: "btn" ok, "btt" no
  - Mai numeri senza contesto: "Component 3" no
  - Coerenza totale: se si sceglie una convenzione, si applica OVUNQUE
```

---

## 31. Struttura File e Pagine

```
STRUTTURA PROGETTO COMPLETA

project-root/
├── DESIGN.md                          ← questo file
├── design-tokens/
│   ├── colors.json                    Token colori (importabili)
│   ├── typography.json                Token tipografia
│   ├── spacing.json                   Token spaziatura
│   └── shadows.json                   Token ombre
├── components/
│   ├── inputs/
│   │   ├── Button/
│   │   ├── TextField/
│   │   ├── Select/
│   │   └── ...
│   ├── navigation/
│   │   ├── Navbar/
│   │   ├── Sidebar/
│   │   └── ...
│   ├── data/
│   │   ├── Table/
│   │   ├── Card/
│   │   └── ...
│   ├── feedback/
│   │   ├── Toast/
│   │   ├── Modal/
│   │   └── ...
│   └── layout/
│       ├── Container/
│       ├── Grid/
│       └── ...
├── pages/
│   ├── 01-onboarding/
│   ├── 02-auth/
│   ├── 03-dashboard/
│   ├── 04-settings/
│   └── ...
├── flows/
│   ├── flow-registration.md           Documentazione flusso
│   ├── flow-checkout.md
│   └── ...
└── assets/
    ├── icons/                         SVG icon set
    ├── illustrations/                 Illustrazioni UI
    └── images/                        Immagini placeholder
```

---

## 32. Checklist QA Pre-Handoff

```
TOKEN E STILI
  [ ] Ogni colore usa un token semantico, mai hex diretto
  [ ] Ogni testo usa uno stile composto definito
  [ ] Ogni spaziatura usa un token della scala
  [ ] Ogni raggio usa un token radius
  [ ] Ogni ombra usa un token shadow
  [ ] Nessun valore "magico" (13px, 17px, #3a3a3a)

COMPONENTI
  [ ] Tutti gli stati interattivi presenti (default, hover, focus, disabled, loading, error)
  [ ] Auto-layout applicato a tutti i container
  [ ] Proprietà componente usate (mai layer nascosti)
  [ ] Naming coerente (PascalCase componenti, kebab-case layer)
  [ ] Icone consistenti in dimensione e stile

LAYOUT
  [ ] Griglia applicata su ogni frame
  [ ] Contenuto allineato alle colonne
  [ ] Breakpoint mobile e desktop progettati
  [ ] Max-width testo rispettato (prose ≤ 680px)
  [ ] Spaziatura verticale coerente tra sezioni

PROTOTIPO
  [ ] Ogni schermo raggiungibile e con percorso di ritorno
  [ ] Navigazione attiva corrisponde allo schermo corrente
  [ ] Transizioni rispettano i token di durata/easing
  [ ] Empty state presente per viste con dati
  [ ] Error state presente per viste con caricamento
  [ ] Loading state presente per operazioni async

ACCESSIBILITÀ
  [ ] Contrasto AA verificato su tutti i testi
  [ ] Contrasto 3:1 verificato su icone e UI
  [ ] Touch target ≥ 44px su tutti gli interattivi
  [ ] Focus ring visibile su ogni elemento interattivo
  [ ] Gerarchia heading sequenziale (h1→h2→h3)
  [ ] Label visibili su tutti i campi form
  [ ] Alt text definito per tutte le immagini significative
  [ ] Colore MAI unico indicatore di stato

INTERNAZIONALIZZAZIONE
  [ ] Testato con stringhe lunghe (tedesco)
  [ ] Testato con stringhe corte (cinese)
  [ ] Layout non si rompe con +40% testo
  [ ] Date e numeri formattati secondo locale
  [ ] Nessuna flag usata come selettore lingua

DARK MODE
  [ ] Tutti i componenti verificati in dark mode
  [ ] Contrasto AA valido anche in dark mode
  [ ] Immagini e illustrazioni adattate
  [ ] Ombre adattate (o sostituite con bordi)
  [ ] Focus ring visibile anche su sfondo scuro

HANDOFF
  [ ] Tutti i layer nominati (nessun "Frame 237")
  [ ] Auto-layout ovunque (distanze ispezionabili)
  [ ] Asset esportabili marcati
  [ ] Annotazioni per comportamenti non ovvi
  [ ] Cover frame con documentazione flusso
  [ ] Versione indicata nel nome del file/pagina
```

---

## 33. Anti-Pattern — Cosa NON Fare

```
ANTI-PATTERN                              CORREZIONE
─────────────────────────────────────────────────────────────────────────
Usare hex diretto nei componenti          → Usare token semantici
Usare solo placeholder, senza label       → Label SEMPRE visibile
Affidarsi solo al colore per lo stato     → Aggiungere icona + testo
Bottone disabled senza spiegazione        → Tooltip o messaggio che spiega il perché
Modal dentro modal (stacking)             → Riprogettare il flusso, max 1 livello
Carousel come unica navigazione           → Carousel complementare, mai primario
Scroll orizzontale non segnalato          → Indicatore visivo o scrollbar visibile
Hover come unico accesso a funzionalità   → Funzionalità accessibile senza hover
Testo in immagine (non selezionabile)     → Testo HTML reale
Icona sola senza label né tooltip         → Aggiungere label o tooltip
Toast per errori critici                  → Usare Alert inline o Dialog
Infinite scroll senza alternativa         → Aggiungere opzione paginazione
Troncare testo senza tooltip              → Mostrare testo completo su hover
Font size sotto 14px per body             → Minimo 16px body, 14px caption
Auto-play video/audio                     → Sempre muto di default, play manuale
Pop-up al caricamento pagina              → Aspettare interazione o scroll
Form lungo in una sola pagina             → Suddividere in step con stepper
Tab cambia URL senza aggiornare stato     → Tab sincronizzata con URL/stato
Sidebar non collassabile su mobile        → Overlay o hamburger su mobile
Layout fisso che non scala                → Responsive con breakpoint
Animazioni senza rispettare               → Verificare prefers-reduced-motion
   prefers-reduced-motion
Duplicare componenti per dark mode        → Usare variable modes
Nominare layer "Frame 1", "Group 5"       → Nomi semantici sempre
Usare !important nel CSS                  → Rivedere specificità dei selettori
Hardcodare stringhe nell'interfaccia      → Usare sistema di traduzione (i18n)
```

---

## 34. Glossario

```
TERMINE                 DEFINIZIONE
─────────────────────────────────────────────────────────────────────────
Token                   Valore di design atomico (colore, spazio, ombra) riutilizzabile
Primitivo               Token di base (es. gray.500) — mai usato direttamente
Semantico               Token con significato funzionale (es. text.primary)
Breakpoint              Soglia di larghezza dove il layout cambia
Auto-layout             Sistema di layout automatico basato su flex
Component property      Proprietà esposta di un componente (variant, boolean, text)
Instance swap           Sostituzione di un sotto-componente con un altro
Variable mode           Modalità alternativa di una variabile (es. light/dark)
Focus trap              Confinamento del focus tastiera dentro un overlay
Focus ring              Indicatore visivo di focus (anello intorno all'elemento)
Touch target            Area minima toccabile su dispositivi touch
ARIA                    Attributi di accessibilità per screen reader
RTL                     Right-to-left: direzione di lettura (arabo, ebraico)
LTR                     Left-to-right: direzione di lettura (italiano, inglese)
i18n                    Internazionalizzazione: supporto multilingua
Skeleton                Segnaposto animato durante il caricamento dati
Shimmer                 Animazione gradient che simula caricamento
Stagger                 Delay incrementale tra elementi animati in sequenza
CTA                     Call to Action: elemento che invita l'utente a compiere un'azione
Viewport                Area visibile dello schermo
Fold                    Linea sotto la quale il contenuto non è visibile senza scroll
KPI                     Key Performance Indicator: metrica chiave
Prose                   Testo lungo e continuo (articoli, documentazione)
Handoff                 Passaggio del progetto dal design allo sviluppo
Edge case               Scenario limite o non standard da gestire
Happy path              Percorso ideale dell'utente senza errori
Empty state             Vista di un componente/pagina senza dati
Overlay                 Elemento sovrapposto al contenuto (modal, drawer, popover)
Backdrop                Sfondo scurito dietro un overlay
```

---

> **Fine del Design System.**
> Questo file è la fonte unica di verità per tutte le decisioni di design.
> Ogni deviazione deve essere documentata e giustificata.
> Aggiornare la versione e la data ad ogni modifica sostanziale.
