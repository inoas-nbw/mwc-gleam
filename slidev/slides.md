---
theme: unicorn
---
# Gleam Team MWC

Über mich:

- Contributor bei Gleam stdlib und gleam compiler: <https://github.com/gleam-lang/stdlib> <mdi-emoticon-excited />
- Seit 1.1.2023 bei der NetzeBW im NetzLive Team (Elixir)
- Hintergrund: C & Java (ages ago), PHP, JavaScript, Ruby, Dart, Elixir, etwas TypeScript, Gleam, etwas Rust

&nbsp;

***

&nbsp;

Das hier ist nur eine kleine Einführung. Wir werden hauptsächlich hands-on arbeiten.

---

## Beam background

- Processes und Schedulers (distributed green threads) 8m6s bis 9m5s <https://www.youtube.com/watch?v=JvBT4XBdoUE#t=8m6s>
- 0 is zu Millionen websocket connections, pro Benutzer ein connection process
- 12m0s bis 20ms <https://www.youtube.com/watch?v=JvBT4XBdoUE#t=15m30s>
- Pro connection process starten und enden calculation processes.
- Unhandled edgecases (div-by-zero), spezielle zahl 13 in diesem talk => calculcation process crash, aber nicht die anderen Prozesse.
- Auch endlosschleifen blockieren nicht das gesamte System (hier negative Eingabe und die Summenfunktion läuft hier als endlosschleife)

---

## Gleam on Beam

### "Let it crash!?"

1. `Good crashes`: Ein Process muss nicht das gesamte system hinunterziehen. Wenn man auf der BEAM ohne global state arbeitet, kann man crashen und restarten.
   > "Did you try turning it off and on again?"
2. `Bad crashes`: Eine Menge an Fehlern kann allerdings auch schon zur _compile-time_ ausgeschlossen werden, durch _strong static typing_.

&nbsp;

Erlang (und Elixir) auf der Beam erlauben die Architektur von _fault-tolerant-systems_ (_good crashes_).
Gleam auf der Beam schließt eine Menge an Problemen kategorisch bereits zu _compile-time_ aus und verhindert die meisten bad crashes.
Diese hängen meist mit striktem handling von inputs zusammen.

&nbsp;

<sub>Disclaimer: Obviously crashes are *NEVER* good! <mdi-emoticon-poop /></sub>

---

Gleam bringt _type-safety_ auf die targets Beam und JavaScript (eine Sprache für Front- und Backend) ohne große Ausnahmen oder Legacy (wie in TS).

---


<img src="/star-history-2.png" class="rounded drop-shadow-2xl m-10 h-90" />

--

Language Tour: <https://gleam.run/book/tour/index.html>
