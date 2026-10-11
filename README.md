# CFD-Simulation eines nadelgesteuerten Injektors

CFD-Untersuchung des Vermischungsverhaltens von Luft und Wasser in einem Injektor für wasserstoffbetriebene Motoren, mit bewegter Nadelgeometrie.

**Kontext:** Tätigkeit als wissenschaftliche Hilfskraft am Institut InEV, Jade Hochschule, seit 09/2024
**Status:** 🚧 laufend. Es liegen noch keine belastbaren quantitativen Ergebnisse vor.
**Software:** Ansys SpaceClaim, Ansys Fluent (Netzanpassung in Ansys 2024 R2)

## Zielsetzung

Wasserstoffmotoren erfordern eine kontrollierte Gemischbildung innerhalb weniger Millisekunden, bei Nadelhüben von rund 0,35 mm und Betätigungsfrequenzen um 367 Hz. Was im Inneren des Injektors passiert, lässt sich messtechnisch kaum erfassen. Die Simulation soll

- das transiente Vermischungsverhalten von Luft und Wasser über den Öffnungs- und Schließzyklus der beiden Nadeln auflösen,
- klären, wie Nadelbewegung und Auslösereihenfolge die Mischgüte am Auslass beeinflussen,
- ein wiederverwendbares Simulationsmodell mit bewegtem Netz und stabiler Netzqualität über viele Zyklen liefern.

## Aufbau

- Je ein Luft- und ein Wassereinlass, jeweils von einer Nadel freigegeben. Y-förmige Zusammenführung und gemeinsamer, schlanker Auslasskanal.
- Fluidkörper aus dem CAD-Modell. Zur numerischen Robustheit wurden die Einlässe leicht verlängert (ausgebildetes Profil vor dem Nadelbereich) und am Auslass ein zweiter Zylinder als Auslassvolumen ergänzt.
- Unstrukturiertes Netz mit feiner Auflösung in den schmalen Kanälen, an der Y-Zusammenführung und an der Düse. Wandnahe Auflösung wurde nachträglich verfeinert.

## Methodik

- Einphasiges Modell, da Luft und Wasser über eigene Zuströmzonen eintreten und nicht an einer Phasengrenze aufeinandertreffen
- Realizable k-ε
- Zwei unabhängig angesteuerte Nadeln mit Dynamic Mesh. Laut Geometrie löst zuerst Nadel 2 aus, danach Nadel 1.

| Phase | Geschwindigkeit | Dauer | Hub |
|---|---|---|---|
| Öffnen | +0,24 m/s | 1,45 ms | ≈ 0,35 mm |
| Schließen | −0,24 m/s | 1,225 ms | ≈ 0,29 mm |

Periodendauer 2,725 ms, das entspricht rund 367 Hz je Nadel.

## Herausforderung

Die hochfrequente Dynamic-Mesh-Bewegung gekoppelt mit der transienten Vermischung erfordert kleine Zeitschritte und eine robuste Netzqualität über viele Zyklen.

## Repository-Inhalt

Dieses Repository beschreibt Aufbau und Methodik. Ergebnisse werden ergänzt, sobald sie vorliegen. Case-Dateien sind aufgrund der Institutszugehörigkeit nicht enthalten.

Portfolio mit Abbildungen: <https://pouria-kamali.de/projekt-injektor.php>
