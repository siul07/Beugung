# Beugung am Spalt – Interaktive Simulation

Dieses Projekt ist eine interaktive Python-Simulation zur **Beugung am Einzelspalt und Doppelspalt**.  
Sie läuft vollständig im Browser über **Google Colab**, sodass keine lokale Installation von Python nötig ist.

---

## Inhalt

- Simulation der **Beugung am Einzelspalt**
- Simulation der **Beugung am Doppelspalt**
- Einstellbare Parameter:
  - Wellenlänge $\lambda\,$
  - Spaltbreite $\a\,$
  - Spaltabstand $\d$ (nur Doppelspalt)
  - Schirmabstand $\L$
  - beobachteter Bereich auf dem Schirm (x-Bereich)
- Darstellung von:
  - 1D-Intensitätsverlauf $\I(x)\$
  - 2D-Beugungsmuster (als „Bild“)
  - verwendeten **Formeln** direkt unter der Simulation
  - aktuell eingestellten **Parametern mit Einheiten**

---

## Simulation im Browser starten

Du kannst die Simulation direkt in Google Colab öffnen:

[[➡ Simulation in Google Colab starten](HIER_COLAB_LINK_EINFÜGEN](https://colab.research.google.com/drive/16wfxkAPTMqF0-s_rcjNquizmbn97KUZ8#scrollTo=6wdlRiDFydXV))


---

## Physikalischer Hintergrund

### Beugung am Einzelspalt (Fraunhofer-Näherung)

Wir betrachten einen Spalt mit Breite $a$ in einem Abstand $L$ von einem Schirm.  
Für kleine Winkel (Fraunhofer-Beugung) kann man die Intensitätsverteilung auf dem Schirm durch


$I(x) = I_0 \left( \frac{\sin \beta}{\beta} \right)^2$


beschreiben, mit

\[
\beta = \frac{\pi a x}{\lambda L}.
\]

- $a$: Spaltbreite  
- $\lambda$: Wellenlänge des Lichts  
- $L$: Abstand Spalt–Schirm  
- $x$: Position auf dem Schirm  
- $I_0$: maximale Intensität (Zentrum des Hauptmaximums)

Die Simulation berechnet diese Intensität als Funktion von $x$ und zeigt:

- den 1D-Plot $I(x)$  
- ein 2D-Bild, das das Beugungsmuster visualisiert.

---

### Doppelspalt (Interferenz + Beugung)

Beim Doppelspalt mit Spaltbreite $a$ und Spaltabstand $d$ erhält man ein Muster aus:

- einer schnellen **Interferenzstruktur** (helle und dunkle Streifen),  
- eingehüllt in die **Einzelspalt-Beugung**.

Die Intensität kann näherungsweise beschrieben werden durch:

\[
I(x) = I_0 \cos^2\!\left(\frac{\pi d x}{\lambda L}\right)
       \left( \frac{\sin \beta}{\beta} \right)^2,
\quad \beta = \frac{\pi a x}{\lambda L}.
\]

- $d$: Abstand der Spaltmitten  
- der $\cos^2$-Term beschreibt die Interferenz der beiden Spalte  
- der $\left(\frac{\sin \beta}{\beta}\right)^2$-Term die Beugung eines einzelnen Spalts

In der Simulation kann zwischen **Einzelspalt** und **Doppelspalt** umgeschaltet werden.

---

## Bedienung der Simulation (Colab)

Im Notebook werden folgende Elemente angezeigt:

- **Radiobutton „Aufbau“**:
  - `Einzelspalt`
  - `Doppelspalt`
- **Slider**:
  - `λ [nm]` – Wellenlänge des Lichts $\lambda$
  - `a [µm]` – Spaltbreite $a$
  - `d [µm]` – Spaltabstand $d$ (nur relevant im Doppelspalt)
  - `L [m]` – Abstand Spalt–Schirm $L$
  - `x_max [mm]` – halbe Breite des beobachteten Schirmbereichs  
    (es wird von $-x_\text{max}$ bis $+x_\text{max}$ geplottet)

Nach jeder Änderung der Parameter werden automatisch aktualisiert:

1. der **Intensitätsverlauf** $I(x)$ als 1D-Plot  
2. das **2D-Beugungsmuster** (als Farbkarte)  
3. ein Block mit den **aktuell eingestellten Parametern** (mit Einheiten)  
4. der passende **Formelblock**:
   - Einzelspalt-Formel oder
   - Doppelspalt-Formel

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
4. Darstellung der Parameter und Formeln über `IPython.display.Markdown` und `Math`.

---

## Mögliche Erweiterungen

Ideen für zukünftige Erweiterungen:

- polychromatisches Licht (Überlagerung mehrerer Wellenlängen)
- Simulation von Mehrfachspalten oder Gittern (Beugung am Gitter)
- Einbau von Linsen (Fourieroptik, Fokuslage)
- Vergleich mit experimentellen Daten (z.B. aus Schulversuchen)

---

## Lizenz

Dieses Projekt darf für schulische und private Zwecke frei verwendet werden.  
Eine kommerzielle Nutzung ist nur nach Rücksprache erlaubt.
