---
kernelspec:
  name: python3
  display_name: 'Python 3'
---

# Geometrische Interpretation: Sekante und Tangente

Im vorigen Abschnitt haben wir den Differenzenquotienten als mittlere Änderungsrate
und den Differentialquotienten als momentane Änderungsrate kennengelernt. In diesem
Kapitel interpretieren wir beide Begriffe geometrisch. Das liefert uns nicht nur ein
tieferes Verständnis der Ableitung, sondern auch die entscheidende Brücke zur
**numerischen Differentiation**: Was wir analytisch als Grenzwert beschreiben, werden
wir numerisch durch einen Differenzenquotienten mit kleinem, aber endlichem $\Delta x$
approximieren.

## Lernziele

```{admonition} Lernziele
:class: attention
* [ ] Sie können den **Differenzenquotienten** geometrisch als Steigung einer
  **Sekante** interpretieren.
* [ ] Sie können den **Differentialquotienten** geometrisch als Steigung einer
  **Tangente** interpretieren.
* [ ] Sie verstehen, wie die Sekante beim Grenzübergang $\Delta x \to 0$ in die
  Tangente übergeht.
* [ ] Sie können erklären, warum ein kleiner, aber endlicher Differenzenquotient
  eine Näherung für die Ableitung liefert und wo dabei ein Fehler entsteht.
```

## Der Differenzenquotient als Steigung der Sekante

Bisher haben wir zwei verschiedene Kontrollpunkte auf der Autobahn oder
allgemein zwei verschiedene Ursachen $x_1$ und $x_2$ betrachtet. Betrachten wir
die Punkte $(x_1, f(x_1))$ und $(x_2, f(x_2))$ rein geometrisch, also mit ihren
Koordinaten $(x_1, y_1)$ und $(x_2, y_2)$, so lautet der Differenzenquotient

\begin{equation*}
\frac{f(x_2) - f(x_1)}{x_2 - x_1} = \frac{y_2 - y_1}{x_2 - x_1} = 
\frac{\Delta y}{\Delta x}.
\end{equation*}

Verbinden wir die beiden Punkte $(x_1, y_1)$ und $(x_2, y_2)$ durch eine Gerade,
dann ist der Differenzenquotient die **Steigung** dieser Gerade. Diese spezielle
Gerade, die zwei Punkte eines Funktionsgraphen miteinander verbindet, wird
**Sekante** genannt.

```{admonition} Was ist ... die Sekante?
:class: note
Die **Sekante** ist eine Gerade, die den Graphen einer Funktion $f$ in zwei
Punkten $(x_1, f(x_1))$ und $(x_2, f(x_2))$ schneidet. Ihre Steigung ist
gleich dem Differenzenquotienten:
\begin{equation*}
m_\text{s} = \frac{f(x_2) - f(x_1)}{x_2 - x_1} = \frac{\Delta y}{\Delta x}.
\end{equation*}
```

In der obigen Definition werden allgemein zwei Punkte $(x_1, y_1)$ und $(x_2,
y_2)$ betrachtet. Im Folgenden möchten wir einen der beiden Punkte fixieren und
nur den zweiten Punkt für die Sekante variieren. Wir notieren den fixierten
Punkt als $(x_0, y_0)$ und den variablen, zweiten Punkt mit $(x,y)$. Damit
ist der Differenzenquotient und die Steigung der Sekante

\begin{equation*}
m_{\text{s}} = \frac{f(x) - f(x_0)}{x - x_0} = \frac{y - y_0}{x - x_0} =
\frac{\Delta y}{\Delta x}.
\end{equation*}

Nun untersuchen wir die Beispielfunktion

\begin{equation*}
f(x)=x^2-2x+3
\end{equation*}

an der Stelle $x_0=2$.

```{admonition} Mini-Übung
:class: tip
Gegeben sei die Funktion $f(x) = x^2 - 2x + 3$ und der fixierte Punkt $(2, 3)$,
also $x_0 = 2$ und $y_0 = 3$. Erstellen Sie ein Python-Programm, das den
Differenzenquotienten bzw. die Sekantensteigung für die Intervalle

1. $[2, 4]$, also $x_0=2$ mit $\Delta x = 2$,
2. $[2, 3]$, also $x_0=2$ mit $\Delta x = 1$,
3. $[2, 2.5]$, also $x_0=2$ mit $\Delta x = 0.5$,
4. $[2, 2.1]$, also $x_0=2$ mit $\Delta x = 0.1$ und
5. $[2, 2.01]$, also $x_0=2$ mit $\Delta x = 0.01$

berechnet und als Tabelle ausgibt.

Was vermuten Sie: Welchem Wert nähert sich die Sekantensteigung an, je kleiner
das Intervall wird?
```

```{code-cell} python
# Code-Zelle
```

````{admonition} Lösung
:class: tip
:class: dropdown
```python
# Eingabe
def f(x):
    return x**2 - 2*x + 3

x0 = 2
y0 = 3

# Verarbeitung und Ausgabe
print('Delta x \t| Differenzenquotient')
for delta_x in [2, 1, 0.5, 0.1, 0.01]:
    # Berechnung Differenzenquotient
    x = x0 + delta_x
    y = f(x)
    differenzenquotient = (y-y0) / (x - x0)

    # Ausgabe als Tabelle
    print(f'{delta_x:1.2f} \t| {differenzenquotient:.4f}')
```
Bei kleineren Intervallen $Delta x$ scheint der Differenzenquotient gegen $2$ zu streben.
````

Die folgende interaktive Abbildung zeigt den Graphen der Beispielfunktion mit
Sekanten. Mit dem Schieberegler können wir den zweiten Punkt variieren und
sehen, wie sich die Steigung der Sekante ändert.

<!-- markdownlint-disable MD033 -->
<div id="sekante-applet">
<iframe
  src="https://gramschs.github.io/thm_anm_de_assets/interactive/chapter04/sekante-tangente-svg.html"
  width="100%"
  frameborder="0"
  scrolling="no">
</iframe>
</div>
<!-- markdownlint-enable MD033 -->

```{admonition} Mini-Übung
:class: tip
Gegeben sei die Funktion $f(x) = x^2$.

1. Berechnen Sie den Differenzenquotienten (= Sekantensteigung) im Intervall $[1, 3]$.
2. Berechnen Sie den Differenzenquotienten im Intervall $[1, 2]$.
3. Berechnen Sie den Differenzenquotienten im Intervall $[1, 1.5]$.
4. Was vermuten Sie: Welchem Wert nähert sich die Sekantensteigung an, je kleiner
   das Intervall wird?
```

```{admonition} Lösung
:class: tip
:class: dropdown
1. $\dfrac{3^2 - 1^2}{3 - 1} = \dfrac{8}{2} = 4$

2. $\dfrac{2^2 - 1^2}{2 - 1} = \dfrac{3}{1} = 3$

3. $\dfrac{1.5^2 - 1^2}{1.5 - 1} = \dfrac{1.25}{0.5} = 2.5$

4. Die Sekantensteigung nähert sich dem Wert $2$ an – das ist die Ableitung
   $f'(x) = 2x$ an der Stelle $x = 1$.
```

```{dropdown} Video zu "Mittlere Änderungsrate" von Mathematrick
<iframe width="560" height="315" src="https://www.youtube.com/embed/sXxK-JATrc0?si=bdcHhSJOUHSl3fNg"
title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media;
gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```

## Der Differentialquotient als Steigung der Tangente

Während der Differenzenquotient die Steigung einer Sekante zwischen zwei Punkten
eines Funktionsgraphen beschreibt, gibt der Differentialquotient die Steigung
der **Tangente** an einem bestimmten Punkt des Graphen an.

```{admonition} Was ist ... die Tangente?
:class: note
Die **Tangente** ist eine Gerade, die den Graphen der Funktion $f$ an einem
bestimmten Punkt $(x_0, f(x_0))$ berührt. Ihre Steigung ist gleich dem
Differentialquotienten (der Ableitung) an dieser Stelle:
$$
m_\text{Tangente} = f'(x_0) = \lim_{\Delta x \to 0} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}.
$$
```

Mathematisch gesehen: Wenn der Abstand $\Delta x$ zwischen den beiden x-Werten
$x_0$ und $x_0 + \Delta x$ gegen Null geht, nähert sich die Sekante immer mehr
der Tangente an. Die folgende Abbildung veranschaulicht diesen Grenzübergang.

```{code-cell} python
:tags: [remove-input]
import numpy as np
import plotly.express as px
import plotly.graph_objects as go

# --- Funktion und Ableitung ---
def f(x):
    return x**2 - 2*x + 3

def df(x):
    return 2*x - 2

# --- Parameter ---
x0 = 2.0
x_plot = np.linspace(0, 4, 300)
delta_x_values = [2.0, 1.5, 1.0, 0.5, 0.2, 0.05]

# --- Farben via Plotly Express Farbpalette ---
colors = px.colors.qualitative.Plotly[:len(delta_x_values)]

# --- Basisfigur: Funktion und Tangente via px.line ---
df_base = {
    "x": np.concatenate([x_plot, x_plot]),
    "y": np.concatenate([
        f(x_plot),
        f(x0) + df(x0) * (x_plot - x0)
    ]),
    "Kurve": (
        ["f(x) = x² - 2x + 3"] * len(x_plot) +
        [f"Tangente (Δx → 0), Steigung = {df(x0):.2f}"] * len(x_plot)
    )
}

fig_base = px.line(
    df_base, x="x", y="y", color="Kurve",
    color_discrete_map={
        "f(x) = x² - 2x + 3": "black",
        f"Tangente (Δx → 0), Steigung = {df(x0):.2f}": "green"
    }
)
# Tangente gestrichelt
fig_base.data[1].line.dash = "dash"

# --- Sekanten und Slider-Logik via go ---
fig = go.Figure(fig_base.data)

for i, dx in enumerate(delta_x_values):
    slope = (f(x0 + dx) - f(x0)) / dx
    fig.add_trace(go.Scatter(
        x=x_plot,
        y=f(x0) + slope * (x_plot - x0),
        mode="lines",
        name=f"Sekante Δx = {dx}, Steigung = {slope:.2f}",
        line=dict(color=colors[i], width=1.5),
        visible=(i == 0)
    ))

# Entwicklungspunkt
fig.add_trace(go.Scatter(
    x=[x0], y=[f(x0)],
    mode="markers",
    name=f"Entwicklungspunkt x₀ = {x0}",
    marker=dict(color="black", size=10),
    showlegend=True
))

# --- Slider ---
n_fixed = 2      # Funktion + Tangente (immer sichtbar)
n_sekanten = len(delta_x_values)
n_punkt = 1      # Entwicklungspunkt (immer sichtbar)

steps = []
for i in range(n_sekanten):
    visibility = (
        [True] * n_fixed +
        [j == i for j in range(n_sekanten)] +
        [True] * n_punkt
    )
    steps.append(dict(
        method="update",
        args=[{"visible": visibility}],
        label=f"Δx = {delta_x_values[i]}"
    ))

fig.update_layout(
    sliders=[dict(
        active=0,
        steps=steps,
        currentvalue=dict(prefix="Δx = ", font=dict(size=14)),
        pad=dict(t=50)
    )],
    title="Sekante nähert sich der Tangente: Δx → 0",
    xaxis_title="x",
    yaxis_title="f(x)",
    yaxis=dict(range=[-1, 12]),
    legend=dict(x=0.01, y=0.99),
    height=520,
    template="plotly_white"
)

fig.show()
```

Man erkennt deutlich: Je kleiner $\Delta x$ wird, desto näher liegt die Sekante
an der Tangente. Im Grenzfall $\Delta x \to 0$ fallen beide zusammen.

Geometrisch ist die Tangente die **beste lineare Näherung** der Funktion in der
unmittelbaren Umgebung des Punktes $(x_0, f(x_0))$.

```{dropdown} Video zu "Differentialquotient" von Mathematrick
<iframe width="560" height="315" src="https://www.youtube.com/embed/_L6wmTzod_I?si=Fj3jbGIOcc3mC4wc"
title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write;
encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```

```{dropdown} Video zu "Ableitung" von Mathematische Methoden
<iframe width="560" height="315" src="https://www.youtube.com/embed/FW7Vd1VI3uw?si=Ij7j2mb5CIKNYUEH"
title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write;
encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```

## Von der Sekante zur numerischen Differentiation

Die geometrische Betrachtung führt uns direkt zur zentralen Idee der numerischen
Differentiation. Analytisch berechnen wir die Ableitung als Grenzwert:

$$
f'(x_0) = \lim_{\Delta x \to 0} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}.
$$

In der Praxis liegt jedoch häufig eine der folgenden Situationen vor:

- Die Funktion $f$ ist analytisch zu komplex zum Differenzieren.
- $f$ ist gar nicht als Formel bekannt, sondern nur als Messdaten oder
  Simulationsergebnis.

In diesen Fällen verzichten wir auf den Grenzübergang und **approximieren** die
Ableitung durch einen Differenzenquotienten mit kleinem, aber endlichem $\Delta x$:

$$
f'(x_0) \approx \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}.
$$

Geometrisch ersetzen wir also die Tangente durch eine Sekante – und akzeptieren
dabei einen kleinen Fehler. Wie groß dieser Fehler ist und wie man ihn minimiert,
ist Gegenstand des nächsten Abschnitts über die **Finite-Differenzen-Formeln**.

## Weiteres Lernmaterial

> - [Mittlere Änderungsrate – Studyflix](https://studyflix.de/mathematik/mittlere-aenderungsrate-4021)
> - [Differenzenquotient – Studyflix](https://studyflix.de/mathematik/differenzenquotient-1881)
> - [Momentane Änderungsrate – Studyflix](https://studyflix.de/mathematik/momentane-aenderungsrate-4034)
> - [Differentialquotient – Studyflix](https://studyflix.de/mathematik/differentialquotient-1339)

## Zusammenfassung

| Begriff | Geometrische Interpretation | Formel |
| --- | --- | --- |
| Differenzenquotient | Steigung der Sekante | $\dfrac{f(x_2)-f(x_1)}{x_2-x_1}$ |
| Differentialquotient / Ableitung | Steigung der Tangente | $\lim_{\Delta x \to 0}\dfrac{f(x_0+\Delta x)-f(x_0)}{\Delta x}$ |
| Numerische Näherung | Sekante mit kleinem $\Delta x$ | $\dfrac{f(x_0+\Delta x)-f(x_0)}{\Delta x}$ |

Im nächsten Abschnitt lernen wir verschiedene Varianten dieser numerischen
Näherung kennen: den **Vorwärtsdifferenzenquotienten**, den
**Rückwärtsdifferenzenquotienten** und den **zentralen Differenzenquotienten** –
und analysieren jeweils ihren Approximationsfehler.
