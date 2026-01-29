# ⚽ World Cup 2026 Prediction — Monte Carlo meets modern football

> *Can we predict the World Cup?*
> No.
> *Can we build a model that understands modern football, momentum and tournament chaos better than pure odds?*
> That’s what this project tries to do.

---

## 🌍 Project overview

This repository contains a **Monte Carlo simulation of the FIFA World Cup 2026**, combining:

* A **machine learning match model** (Gradient Boosting)
* **FIFA ranking & points**
* **Recent form** (smoothed last-5 matches)
* **Head-to-head history**
* **Penalty shootout performance**
* **Tournament variance**
* **Historical achievements with strong recency decay**
* **Modern football strength** (tactical + structural)

The goal is **not** to predict exact results,
but to **estimate realistic championship probabilities** under a **new World Cup format**.

---

## 🏆 Why World Cup 2026 is different

World Cup 2026 is *not* like previous tournaments:

* 🇺🇸🇨🇦🇲🇽 **3 host countries**
* 🏟️ Long travel distances
* 🧠 Greater importance of squad depth & rotation
* 🆕 **New format**:

  * 12 groups of 4 teams
  * 12 group winners qualify directly
  * Best 8 runners-up advance
  * Remaining runners-up play a **play-in round**
  * Then classic knockouts (Round of 16 → Final)

This format introduces **more randomness**, especially for:

* Traditional powers with slow starts
* Teams relying on “one perfect match”
* Physically fragile squads

---

## 📊 High-level pipeline

```text
Raw match data (2000 → present)
        ↓
Feature engineering
        ↓
Gradient Boosting match model
        ↓
Tournament simulation (5,000+ runs)
        ↓
Champion probability distribution
```

Each simulation represents **one possible World Cup universe**.

---

## 🧠 Match model philosophy

A match is decided by:

* **Baseline strength** (FIFA points)
* **Recent momentum** (smoothed form)
* **Tactical maturity** (modern football bonus)
* **Psychology & experience** (recent achievements)
* **Randomness** (increasing with tournament round)

Later rounds are **less predictable** by design.

```python
ROUND_VARIANCE = {
    "group": 12,
    "play-in": 25,
    "round_of_16": 35,
    "quarterfinal": 40,
    "semifinal": 55,
    "final": 60
}
```

The World Cup final is chaos.
The model embraces that.

---

## 🆕 Modern football matters

One key design choice:
**historical success alone is not enough**.

Winning a World Cup in 2002 should not outweigh:

* Tactical structure
* Pressing systems
* Squad automation
* Tournament adaptability

We introduce a **Modern Football Strength** bonus:

```python
MODERN_TEAMS = {
    "Argentina": 30,
    "Spain": 26,
    "France": 24,
    "England": 23,
    "Morocco": 23,
    "Germany": 21,
    "Croatia": 20,
    "Japan": 19,
    "Netherlands": 19,
    "Senegal": 18,
    "Portugal": 18,
    "Belgium": 16,
    "Uruguay": 15,
    "Brazil": 12
}
```

This is **not arbitrary**:

* Rewards tactical continuity
* Penalizes talent-without-system
* Reflects post-2018 international football reality

---

## 📈 Example output (Champion probabilities)

After 5,000 simulations:

```text
Argentina        19.9%
France            8.7%
Spain             6.9%
England           6.1%
Morocco           5.8%
Germany           5.4%
Portugal          4.5%
Japan             3.9%
Netherlands       3.6%
Brazil            3.2%
```

### 🧐 But betting houses say Spain is favourite…

Yes — and that’s **exactly the point**.

Bookmakers price:

* Market sentiment
* Volume
* Risk balancing

This model asks a different question:

> *Which teams are best adapted to modern tournament football under extreme variance?*

And the answer consistently leans towards:

* **Argentina**
* **France**
* **Spain**
* **England**
* **Morocco (dark horse)**

---

## 🏔️ A mental picture

Imagine the World Cup as a mountain.

* Some teams climb fast but fall early
* Some climb slowly but never stop
* Some reach the summit often, but not always first

Argentina doesn’t always win.
But **they reach the final stages in most simulated universes**.

That’s what matters.

---

## 🇺🇸🇨🇦🇲🇽 Hosts & regional context

Host teams are treated carefully:

* **United States**

  * Athletic, improving, home support
  * Still tactically inconsistent

* **Mexico**

  * Experience & crowd advantage
  * Declining generation → penalized

* **Canada**

  * Intensity & speed
  * Limited tournament experience

None receive artificial “host boosts”, only **structural advantages** reflected in data.

---

## ⚠️ Limitations (important)

This project is **not omniscient**.

### Known limitations:

* No explicit player-level injuries
* No real-time squad selection
* Coaching changes not dynamically modeled
* Chemistry is inferred, not measured
* FIFA rankings are imperfect proxies
* Some national teams evolve rapidly (Japan, Morocco)

And most importantly:

> **Football is not deterministic.**

If it were, Greece 2004 would not exist.

---

## 🔮 Future improvements

Planned or possible extensions:

* 🧍 Player-level embeddings (club form → national team)
* 🧠 Coaching style vectors
* 🗺️ Travel & climate fatigue modeling
* 🟥 Discipline risk (cards & suspensions)
* 📊 Dynamic odds comparison vs bookmakers
* 🏟️ Stadium-specific performance effects

---

## ❤️ Final thought

This project is not about being *right*.

It’s about:

* Thinking clearly
* Respecting uncertainty
* Modeling football as the chaotic, beautiful game it is

If your favorite team wins in the simulation — great.
If it doesn’t — that’s football.

---

## ⚽ Because in the end…

> *The ball is round, the match lasts 90 minutes, and anything can happen.*
