+++
title = 'Standardisierte Commits'
date = 2024-06-16T12:40:24+02:00
draft = false 
+++

In der Softwareentwicklung spielen Versionskontrollsysteme wie Git eine zentrale Rolle.
Ein besonders wichtiger Aspekt im Umgang mit Git ist die Formulierung der Commit-Nachrichten.
Dieser Aspekt wird häufig vernachlässigt, was die Zusammenarbeit im Team erschwert und die Nachverfolgbarkeit von Änderungen beeinträchtigt.

Standardisierte Commit-Nachrichten, die einer klar definierten Struktur und Syntax folgen, bieten zahlreiche Vorteile, die zur Effizienz und Qualität der Softwareentwicklung beitragen.

Einer der am weitesten verbreiteten Standards ist [Konventionelle Commits](https://www.conventionalcommits.org/de/v1.0.0/).
Dieser Standard funktioniert wie folgt: Jede Commit-Nachricht beginnt mit einem Typ, gefolgt von einer kurzen, prägnanten Beschreibung der Änderung.
Optional können zusätzliche Informationen wie ein Umfang oder ein ausführlicherer Textabschnitt hinzugefügt werden.
In der Fußnote der Commit-Nachricht können auch Referenzen zu Pull Requests oder anderen relevanten Informationen hinzugefügt werden.

{{< video src="project.mp4" >}}
#### Häufigverwendete Typen von konventionellen Commits:

- `feat`: Hinzufügen einer neuen Funktion.
- `fix`: Behebung eines Fehlers.
- `docs`: Änderungen an der Dokumentation.
- `style`: Änderungen, die das Format betreffen (keine inhaltlichen Code-Änderungen).
- `refactor`: Code-Änderungen, die weder Fehler beheben noch Funktionen hinzufügen.
- `test`: Hinzufügen oder Ändern von Tests.
- `chore`: Wartungsaufgaben, die keine Änderungen am Code oder den Tests beinhalten.
- `perf`: Änderungen zur Verbesserung der Leistung.
- `build`: Änderungen, die das Build-System oder externe Abhängigkeiten betreffen.
- `ci`: Änderungen an den Continuous Integration-Konfigurationsdateien und Skripten.

#### Beispiel-Commit-Nachrichten

- `feat(auth): implement OAuth2 login`
- `docs(README): add installation instructions`
- `style(header): align header elements to the center`
- `refactor(api): simplify request handling logic`


### Vorteile von [Konventionellen Commits](https://www.conventionalcommits.org/de/v1.0.0/)

#### Versionnummer-Generierung

[Konventionelle Commits](https://www.conventionalcommits.org/de/v1.0.0/) ermöglichen ein automatisiertes, [semantisches Versionieren](https://semver.org/lang/de/), ein weit verbreiteter Standard für Software-Versionierung. 
Durch das Parsen von Commit-Nachrichten können Tools die Art der Änderungen (z.B. neue Funktionen, Fehlerbehebungen, Breaking Changes) bestimmen und automatisch die Versionsnummern entsprechend aktualisieren.

#### Changelog-Generierung

Tools wie [Semantic Release](https://semantic-release.gitbook.io/semantic-release) können Commit-Nachrichten analysieren und einen detaillierten Changelog erstellen, der alle in einer bestimmten Version vorgenommenen Änderungen zusammenfasst.

#### Filterbarkeit
Möglichkeit nach Commit-Typen zu sortieren, um relevante Änderungen zu finden.

#### Klare Kommunikation

[Konventionelle Commits](https://www.conventionalcommits.org/de/v1.0.0/) fördern eine klare und prägnante Kommunikation. Das standardisierte Format stellt sicher, dass jeder den Zweck jedes Commits und dessen Auswirkungen auf das Projekt versteht.

