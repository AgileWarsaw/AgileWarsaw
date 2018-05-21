Tu spisujemy pomysły na działanie listo-obecnościowego bota 

# Pomysł 1 (wersja mini) 
Bot mógłby dostać listę uczestników spotkania oraz limit i wypluć listę do kliknięcia "Yes". 
1. lista "Yes" to lista chętnych, którzy nie mają no-show w kolejności fifo
1. pewnie powinien kumać ile osób już ma Yes, a ile na waitliście (i tylko uzupełniać do limitu) 
1. można dodać ignorowanie "odpracowanych" no-show (jak odpracowujemy?) 
1. można dodać listę rezerwową, czyli iluś następnych osób bez no-show lub z odpracowanymi no-showami 
1. można w razie za małej liczby "czystych" uczestników jakoś wybranych no-showów (fifo po liczbie no-show) 
1. można brać id meetupa a nie listę ludzi

# Pomysł 2 (wersja super mini) 
Bot mógłby dostać listę uczestników spotkania i wypluć listę z policzonymi no-showami 
1. można dodać odprawcowywanie
1. boot mógłby zmieniać status na "Yes" i pisać wiadomość na priv do osoby, której zmienił status.

# Pomysł 3 (full wypas) 
Bot mógłby wyliczać listę gości do zaproszenia (tak, jak w pomyśle 1) i sam im klikać "Yes" 
1. pewnie warto zachować jakąś historię, by ew naprawić jak bot popsuje. 
1. można dodać sprawdzanie co jakiś czas (co godzinę?) i dodawanie następnych z listy jeśli miejsce się zwolniło
1. można dodać jakieś zgrabne informowanie tych pominiętych, że zostali pominięci
