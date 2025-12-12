# Beugung am Spalt – Interaktive Simulation

Dieses Projekt ist eine interaktive Python-Simulation zur Beugung am Einzelspalt, Doppelspalt und einem vereinfachten Mehrfachspalt/Gitter.  
Sie läuft vollständig im Browser über Google Colab, sodass keine lokale Installation von Python nötig ist.

---

## Inhalt

- Simulation der Beugung am Einzelspalt
- Simulation der Beugung am Doppelspalt
- Simulation eines Mehrfachspalts/Gitters mit $N$ Spalten
- Einstellbare Parameter:
  - Wellenlänge $λ$
  - Spaltbreite $a$
  - Spaltabstand/Gitterkonstante $d$
  - Anzahl der Spalte $N$ (für das Gitter)
  - Schirmabstand $L$
  - beobachteter Bereich auf dem Schirm $x$
- Darstellung von:
  - 1D-Intensitätsverlauf $I(x)$
  - 2D-Beugungsmuster (als „Bild“)
  - verwendeten Formeln direkt unter der Simulation
  - aktuell eingestellten Parametern mit Einheiten
- Vergleich mit experimentellen Daten:
  - Eingabe von gemessenen Maxima-Positionen
  - Berechnung der theoretischen Positionen
  - Berechnung der prozentualen Abweichung

---

## Simulation im Browser starten

Du kannst die Simulation direkt in Google Colab öffnen:

[➡ Simulation in Google Colab starten](https://colab.research.google.com/drive/16wfxkAPTMqF0-s_rcjNquizmbn97KUZ8#scrollTo=6wdlRiDFydXV)

---

## Physikalischer Hintergrund

### Beugung am Einzelspalt (Fraunhofer-Näherung)

Wir betrachten einen Spalt mit Breite $a$ in einem Abstand $L$ von einem Schirm.  
Für kleine Winkel (Fraunhofer-Beugung) kann man die Intensitätsverteilung auf dem Schirm durch

$I(x)=I_0\left(\frac{\sin\beta}{\beta}\right)^2$

beschreiben, mit

$\beta=\frac{\pi a x}{\lambda L}$.

- $a$: Spaltbreite  
- $λ$: Wellenlänge des Lichts  
- $L$: Abstand Spalt–Schirm  
- $x$: Position auf dem Schirm  
- $I_0$: maximale Intensität (Zentrum des Hauptmaximums)

Die Simulation berechnet diese Intensität als Funktion von $x$ und zeigt:

- den 1D-Plot $I(x)$  
- ein 2D-Bild, das das Beugungsmuster visualisiert.

---

### Doppelspalt (Interferenz + Beugung)

Beim Doppelspalt mit Spaltbreite $a$ und Spaltabstand $d$ erhält man ein Muster aus:

- einer schnellen Interferenzstruktur (helle und dunkle Streifen),  
- eingehüllt in die Einzelspalt-Beugung.

Die Intensität kann näherungsweise beschrieben werden durch:

$I(x)=I_0\cos^2\left(\frac{\pi d x}{\lambda L}\right)\left(\frac{\sin\beta}{\beta}\right)^2,\quad\beta=\frac{\pi a x}{\lambda L}$.

- $d$: Abstand der Spaltmitten  
- der $\cos^2$‑Term beschreibt die Interferenz der beiden Spalte  
- der $\left(\frac{\sin\beta}{\beta}\right)^2$‑Term die Beugung eines einzelnen Spalts

In der Simulation kann zwischen Einzelspalt und Doppelspalt umgeschaltet werden.

---

### Mehrfachspalt/Gitter

Für einen Mehrfachspalt oder ein Beugungsgitter mit $N$ Spalten und Spaltabstand $d$ erhält man eine schärfere Interferenzstruktur.  
Im vereinfachten Modell wird die Intensität beschrieben durch

$I(x)=I_0\left(\frac{\sin\beta}{\beta}\right)^2\left(\frac{\sin(N\delta)}{\sin\delta}\right)^2$

mit

$\beta=\frac{\pi a x}{\lambda L},\quad\delta=\frac{\pi d x}{\lambda L}$

und der Gittergleichung

$d\sin\theta=mλ,\quad m\in\mathbb{Z},\quad\theta\approx x/L$.

Damit lassen sich Lage und Schärfe der Maxima für ein Gitter qualitativ untersuchen.

---

## Vergleich mit experimentellen Daten

Im unteren Teil des Notebooks gibt es eine Sektion **„Vergleich mit Messdaten“**.  
Dort können z.B. aus einem Doppelspalt- oder Gitterversuch folgende Werte eingegeben werden:

- gemessene Maxima-Positionen $x_\text{mess}$ in mm (z.B. `-8.2, -4.1, 0.0, 4.2, 8.3`)
- zugehörige Ordnungszahlen $m$ (z.B. `-2, -1, 0, 1, 2`)
- Wellenlänge $λ$ in nm
- Spaltabstand/Gitterkonstante $d$ in µm
- Schirmabstand $L$ in m

Das Notebook berechnet daraus:

1. theoretische Positionen $x_\text{theo}$ (kleiner Winkel: $x_\text{theo}=mλL/d$)
2. die Abweichung
   - absolut: $Δx=x_\text{mess}-x_\text{theo}$
   - relativ (prozentual):  
     $\text{Abweichung}=\dfrac{|x_\text{mess}-x_\text{theo}|}{|x_\text{theo}|}\cdot100\%$
3. eine Tabelle mit:
   - Ordnung $m$
   - $x_\text{mess}$ [mm]
   - $x_\text{theo}$ [mm]
   - $Δx$ [mm]
   - prozentuale Abweichung [%]

So können Messdaten aus Schulversuchen direkt mit der Theorie verglichen werden.

---

## Bedienung der Simulation (Colab)

Im Notebook werden folgende Elemente angezeigt:

- Radiobutton „Aufbau“:
  - Einzelspalt
  - Doppelspalt
  - Gitter (Mehrfachspalt)
- Slider:
  - `λ [nm]` – Wellenlänge des Lichts $λ$
  - `a [µm]` – Spaltbreite $a$
  - `d [µm]` – Spaltabstand/Gitterkonstante $d$
  - `N (Gitter)` – Anzahl der Spalte $N$
  - `L [m]` – Abstand Spalt–Schirm $L$
  - `x_max [mm]` – halbe Breite des beobachteten Schirmbereichs  
    (es wird von $-x_{max}$ bis $+x_{max}$ geplottet)

Nach jeder Änderung der Parameter werden automatisch aktualisiert:

1. der Intensitätsverlauf $I(x)$ als 1D-Plot  
2. das 2D-Beugungsmuster (als Farbkarte)  
3. ein Block mit den aktuell eingestellten Parametern (mit Einheiten)  
4. der passende Formelblock:
   - Einzelspalt-Formel
   - Doppelspalt-Formel
   - Mehrfachspalt/Gitter-Formel

Im Abschnitt **„Vergleich mit Messdaten“** können gemessene Maxima-Positionen und Ordnungszahlen $m$ eingetragen werden; die Simulation erstellt dann automatisch eine Tabelle mit den Abweichungen.

---

## Technische Umsetzung

Die Simulation verwendet:

- Python
- NumPy für Berechnungen
- Matplotlib für die Plots
- ipywidgets für die interaktiven Slider und Radiobuttons
- Google Colab als Ausführungsumgebung (läuft im Browser)

Die wesentlichen Schritte:

1. Berechnung der Intensität auf einem 1D-Gitter von Schirmpositionen $x$.
2. Normierung und „Stapelung“ der 1D-Intensität, um ein 2D-Beugungsmuster zu erzeugen.
3. Darstellung von 1D- und 2D-Plot mit Matplotlib.
4. Darstellung der Parameter und Formeln über IPython.display.Markdown und Math.
5. Vergleich von Messwerten mit den theoretischen Positionen (inkl. prozentualer Abweichung).

---

## Mögliche Erweiterungen

Weitere Ideen für zukünftige Erweiterungen:

- polychromatisches Licht (Überlagerung mehrerer Wellenlängen)
- Einbau von Linsen (Fourieroptik, Fokuslage)
- automatische Anpassung von Parametern an Messdaten (Fit)
- Export von Daten (CSV) zur weiteren Auswertung

---

## Lizenz

Dieses Projekt darf für schulische und private Zwecke frei verwendet werden.  
Eine kommerzielle Nutzung ist nur nach Rücksprache erlaubt.
