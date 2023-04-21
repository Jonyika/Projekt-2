Projekt  Power BI

Cílem projektu je vizualizace datasetu na téma Pracovní neschopnost v ČR v letech 2015-2022. Použila jsem následující datové sady z Portálu otevřených dat ČR:
-	PN dle krajů – statistika ukončených PN rozdělená podle krajů a délky trvání
-	PN dle diagnózy – statistika ukončených PN rozdělená podle krajů a délky trvání – statistika ukončených případů PN, prostonaných dnů a rozdělená dle diagnóz a pohlaví
-	Počet vyplacených dávek v krajích – počet výplat realizovaný v měsící pro zaměstance a OSVČ nemocensky pojištěné podle krajů
-	Číselník krajů

Na začátek jsem provedla transformaci dat do požadovaného tvaru, tj. změna datových typů, odebrání sloupců a duplicitních položek.
Pak jsem přistoupila k nadefinování ERD diagramu. Vytvořila jsem si Tabulku dat, kde jsem pomocí DAX funkce CALENDAR vytvořila sloupec se souvislou řadou kalendářních dat. Tato tabulka posloužila pro vytvoření kardinality 1:M s tabulkou PN dle krajů, tabulkou PN dle diagnózy a tabulkou Počet vyplacených dávek v krajích (relace přes sloupec Datum). Další dvě kardinality 1:M jsem vytvořila spojením tabulky Číselník krajů s tabulkou PN dle krajů a tabulkou Počet vyplacených dávek v krajích (relace přes sloupec kraj_kod).

Vizualizaci jsem rozdělila na dvě hlavní části: Diagnózy a Kraje.

1.Diagnózy
V hlavní části jsem pomocí skládaného sloupcového grafu znázornila vývoj počtu pracovních neschopností v jednotlivých diagnózách. Pomocí průřezu jsem přidala Hierarchii dat, která umožňuje zobrazení grafu pro konkrétní rok, čtvrtrok i měsíc.
Abych mohla znázornit celkové počty PN v jednotlivých kalendářních dnech, do Tabulky dat jsem si dosadila další slopec, ve kterém jsem si sečetla  ukončené případy v jednotlivých dnech pomocí DAX funkce CALCULATE a SUM. Pro vizualizaci jsem použila spojnicový graf. Pomocí posuvníku zoomování je možné zobrazit počty detailně pro jednotlivé roky, čvrtroky, měsíce nebo dny.
Na stránku jsem zařadila dvě karty, které zobrazuji hodnotu -  průměrný počet prostonaných dnů u žen a u mužů. Pro výpočet hodnot jsem použila funkci CALCULATE a AVERAGE.

2.Kraje
Do hlavní části jsem opět zařadila skládaný sloupcový graf zobrazující vývoj počtu pracovních neschopností, ale v rozdělení na jednotlivé kraje. Hierarchie dat v průřezu i tady umožňuje zobrazení grafu pro konkrétní rok, čtvrtrok i měsíc.
Tabulka uvádí počet dávek PN v jednotlivých krajích jak pro ženy, tak i pro muže.
Použitím matice jsem zobrazila počet vyplacených dávek PN žen a mužů rozdělených podle jednotlivých typů PN. 

