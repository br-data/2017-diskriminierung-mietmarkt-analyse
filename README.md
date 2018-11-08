# Wir müssen draußen bleiben – Analyse
Enthält eine Dokumentation der Methodik unseres Experiments zur Diskriminierung am Mietmarkt. Diese liegt in Form eines R-Notebooks vor und macht die Berechnungen somit transparent und reproduzierbar.

- **Live**: https://www.hanna-und-ismail.de/

## Verwendung
1. Repository klonen `git clone https://...`
2. `analyse.Rmd` in RStudio öffnen
3. Code-Chunks ausführen
4. `analyse.nb.html` enthält eine [HTML-Version](https://br-data.github.io/2017-diskriminierung-mietmarkt-analyse/analyse.nb.html) des gesamten Prozesses

## Datenquelle
Im Juni und September 2016 haben wir uns in einem automatisierten Prozess auf 6798 Wohnungsannoncen in Berlin, Leipzig, München, Magdeburg, Dortmund, Köln, Nürnberg, Frankfurt, Dresden, Hamburg beworben. Die Absender der 20728 E-Mail-Anfragen unterschieden sich lediglich im Namen, der auf einen deutschen, arabischen, türkischen, italienischen oder polnischen Hintergrund schließen lässt. In ihren sonstigen Eigenschaften waren die Personen identisch – zwischen 20 und 30 Jahre alt, Berufseinsteiger in einer Agentur, mit Anschreiben in perfektem Deutsch. Männer und Frauen waren gleich häufig vertreten.

Auf die Anfragen erhielten wir rund 8000 Antworten, die wir händisch in Kategorien einsortierten. Nur so konnten wir sicher erfassen, ob ein Bewerber zur Wohnungsbesichtigung eingeladen wurde oder nicht. Das Ergebnis ist ein Datensatz, der ein Schlaglicht auf den deutschen Mietwohnungsmarkt wirft, aber zugleich groß genug ist, um signifikante Unterschiede zwischen Nationalitäten, Geschlechtern und Städten zu zeigen.

## Datensatz

Der entstandene Datensatz befindet sich im Ordner `input`. Im Kern besteht der Datensatz aus vier Tabellen:

- **persons.xlsx** - Die 14 fiktiven Personen, die für die Kontaktaufname genutzt wurden sowie deren Name, Geschlecht, Herkunft und Mail-Adresse.
- **confirmations.csv** - Übersicht über alle im Lauf des Versuchs erfolgreich angefragten Wohnungsannoncen. Beinhaltet u.A. die anfragende Person, den Link zur Annonce sowie den zeitlichen Abstand zwischen den Anfragen mit den verschiedenen Profilen.
- **flats.csv** - Beinhaltet die Meta-Daten zu den angefragten Wohnungen. Aus Datenschutzgründen werden Informationen, die Rückschlüsse auf einzelne Wohnungen oder Inserenten zulassen (Ansprechpartner, Adresse, Betreff, Telefonnumer) nicht veröffentlicht.
- **mails.xlsx** - Die Kategorisierung der empfangenen Emails. Es wurde folgendes Codebuch verwendet:

| Kategorie | Umschreibung |
|:-----:|:-----|
| 1 | positv: Zusage eines Besichtigungstermins |
| 2 | positive Tendenz: Ein Besichtigungstermin wird in Aussicht gestellt|
| 3 | Kenntnise: Anfrage wurde zur Kenntnis genommen. Enthält keine Wertung |
| 4 | negativ: Absage |
| 5 | Wohung nicht verwertbar: z.B. Seniorenwohnanlage, WG-Zimmer |
| 6 | Mail nicht verwertbar: keine relevante Aussage (z.B. Newsletter) |
| 7 | Makler-Masche: Versuchtes Umgehen des Besteller-Prinzips |
| 8 | Spam/Scam: Ohne Aussage hinsichtlich der Diskriminierung |


## Statistischer Hintergrund
Neben deskriptiven Berechnungen haben wir ebenso logisitische Regressionen durchgeführt um Erstere abzusichern oder sie direkt in der Berichterstattung zu verwenden. Zusätzlich zur ausführlichen Beschreibung mit Code im R-Notebook `analyse.Rmd`in diesem Repository gibt es eine kompakte Version im [Methodik-Teil](https://www.hanna-und-ismail.de/methodik.html) der Projekt-Website.
