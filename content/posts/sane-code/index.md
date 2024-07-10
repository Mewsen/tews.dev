+++
title = 'Vernünftiger Code'
date = 2024-07-10
draft = false 
+++

# Einleitung

In der Softwareentwicklung ist es entscheidend, Code von hoher Qualität zu schreiben, der sowohl lesbar als auch wartbar ist. Nach langer Überlegung und Reflexion bin ich zu folgenden Punkten gekommen, die aus meiner Erfahrung zu besserer Software führen. Diese sind in einer unsortierten Auflistung dargestellt.

## Verwende Asserts um Programmierfehler zu vermeiden
Im Gegensatz zu erwarteten Betriebsfehlern, die behandelt werden müssen, sind Assertion-Fehler unerwartet. Der einzig richtige Umgang mit fehlerhaftem Code ist ein Absturz. Assertions verwandeln katastrophale Fehler in weniger schwerwiegende Fehler und sind nützlich beim Aufdecken von Fehlern durch Fuzzing.

**Assertions für alle Funktionsargumente und Rückgabewerte, Vor-/Nachbedingungen und Invarianten:** Eine Funktion darf nicht mit ungeprüften Daten arbeiten. Der Zweck einer Funktion ist es, die Korrektheit eines Programms zu erhöhen. Jede Funktion sollte im Durchschnitt mindestens zwei Assertions enthalten.

**Assertions statt Kommentaren:** Verwende offensichtlich wahre Assertions als stärkere Dokumentation, wenn die Bedingung kritisch und überraschend ist.

**Goldene Regel:** Prüfe sowohl den erwarteten positiven Bereich als auch den unerwarteten negativen Bereich. Interessante Fehler treten oft an der Grenze zwischen gültigen und ungültigen Daten auf. Tests müssen daher sowohl mit gültigen als auch mit ungültigen Daten umfassend durchgeführt werden.

## Gute Variablen-, Funktionen-, Klassen- und Modulnamen
Finde die richtigen Substantive und Verben. Gute Namen sind das Wesen guten Codes; sie erfassen, was etwas ist oder tut, und bieten ein klares, intuitives Modell. Sie zeigen, dass du die Domäne verstehst. Nimm dir Zeit, den perfekten Namen zu finden, Substantive und Verben, die zusammenpassen, sodass das Ganze mehr ist als die Summe seiner Teile.

Verkürze Variablennamen nicht, es sei denn, es handelt sich um primitive Ganzzahlen, die als Argumente für Sortierfunktionen oder Matrizenberechnungen verwendet werden. Verwende die richtige Großschreibung für Akronyme (DBConnector, nicht DbConnector).

## Keine Errorwerte ignorieren
Ignorieren von Errorwerten kann zu schwer zu findenden Bugs und unerwartetem Verhalten führen. Es ist wichtig, Fehlerwerte stets zu prüfen und angemessen zu behandeln, um die Zuverlässigkeit und Stabilität des Codes zu gewährleisten. Eine detaillierte Untersuchung dieser Problematik findet sich im [USENIX Paper von Yuan et al.](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-yuan.pdf).

## Ein Codeformatierer verwenden
Die Konsistenz im Codeformat ist entscheidend für die Lesbarkeit und Wartbarkeit von Code. Verwende stets einen automatischen Codeformatierer, um sicherzustellen, dass der Code sauber und einheitlich bleibt. Tools wie Prettier, gofmt oder rustfmt können dabei helfen, den Code standardisiert zu formatieren.

## Unittests
Unittests sind unerlässlich, um sicherzustellen, dass jede Funktion wie erwartet funktioniert. Sie helfen dabei, Fehler frühzeitig zu erkennen und zu beheben, bevor der Code in Produktion geht. Schreibe für jede Funktion umfassende Tests, welche einfach zu erweitern sind, und führe sie vor jedem Commit aus.

## Dokumentation
Gute Dokumentation ist entscheidend für die langfristige Wartbarkeit und Erweiterbarkeit von Softwareprojekten. Dokumentiere alle öffentlichen APIs, komplexen Algorithmen und wichtige Designentscheidungen gründlich. Verwende Tools wie Javadoc oder godoc, um die Dokumentation automatisch zu erstellen.

## Dependencies minimieren
Minimiere die Abhängigkeiten von externen Bibliotheken und Frameworks, um die Komplexität und potenzielle Sicherheitsrisiken zu reduzieren. Jede zusätzliche Abhängigkeit erhöht das Risiko von Inkompatibilitäten und Fehlern.

## CI/CD
Continuous Integration und Continuous Deployment (CI/CD) sind bewährte Methoden, um die Qualität und Zuverlässigkeit von Software zu erhöhen. Setze ein CI/CD-System ein, um automatisierte Tests und Deployments zu ermöglichen und sicherzustellen, dass jede Code-Änderung schnell und zuverlässig integriert wird.

## Versionskontrollsystem (VCS)
Verwende ein Versionskontrollsystem wie Git, um Änderungen am Code nachzuvollziehen und zusammenzuarbeiten. Nutze Branches, um neue Features oder Bugfixes zu entwickeln, und erstelle regelmäßig Commits mit aussagekräftigen Nachrichten ([Standardisierte Commits](/posts/conventional-commits)). Dies erleichtert das Nachverfolgen von Änderungen und das Identifizieren von Fehlern.

## Abstraktionen
Abstraktionen helfen dabei, Komplexität zu verbergen und den Code verständlicher zu machen. Verwende Abstraktionen jedoch sparsam und bewusst, da sie auch die Komplexität erhöhen können. Gute Abstraktionen vereinfachen das Verständnis und die Wartung des Codes.

## Funktionen maximal ~50 Zeilen
Halte Funktionen kurz und fokussiert. Idealerweise sollten Funktionen nicht länger als 50 Zeilen sein. Dies erhöht die Lesbarkeit und Verständlichkeit des Codes und erleichtert das Testen und Debuggen.

## Minimiere Verschachtelungen
Tiefe Verschachtelungen können schwer zu verstehen und zu warten sein. Verwende frühzeitige Rückgaben und [Guard Clauses](https://en.wikipedia.org/wiki/Guard_(computer_science)), um die Tiefe zu minimieren.

## Performance von Anfang an planen
Leistungsoptimierung sollte von Beginn an ein integraler Bestandteil der Entwicklung sein. Identifiziere potenzielle Engpässe und optimiere den Code, bevor er in Produktion geht. Dies verhindert teure Nacharbeiten und Performance-Probleme im späteren Verlauf.

## Kommentare, Dokumentationen und Commitnachrichten immer auf Englisch
Verwende Englisch für alle Kommentare, Dokumentationen und Commitnachrichten, um die Verständlichkeit und Zusammenarbeit in internationalen Teams zu gewährleisten.

## Code um Datenstrukturen designen und nicht anders herum
Gute Datenstrukturen vereinfachen das Design und die Wartung von Code. Der Code sollte um die Datenstrukturen herum entwickelt werden, um Klarheit und Effizienz zu gewährleisten.

## NASA: The Power of 10
1. **Avoid complex flow constructs, such as goto and recursion.**
2. **All loops must have fixed bounds. This prevents runaway code.**
3. **Avoid heap memory allocation.**
4. **Restrict functions to a single printed page.**
5. **Use a minimum of two runtime assertions per function.**
6. **Restrict the scope of data to the smallest possible.**
7. **Check the return value of all non-void functions, or cast to void to indicate the return value is useless.**
8. **Use the preprocessor sparingly.**
9. **Limit pointer use to a single dereference, and do not use function pointers.**
10. **Compile with all possible warnings active; all warnings should then be addressed before release of the software.**

[Link](http://web.eecs.umich.edu/~imarkov/10rules.pdf)

## Minimiere Kommentare
Übermäßige Kommentare deuten oft auf komplexen oder schlecht strukturierten Code hin. Strebe danach, den Code so klar und verständlich wie möglich zu schreiben, sodass Kommentare weitgehend überflüssig werden. Verwende Kommentare nur, um komplexe oder nicht offensichtliche Aspekte zu erklären.
