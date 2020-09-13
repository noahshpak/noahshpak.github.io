---
layout: post
title: Dynamics of Preference Falsification
description: Preference Falsification
summary: The ripple effects of private truths
comments: true
tags: [anthropology, psychology, economics]
---

# Preference Falsification
### Scenarios

### Complacency

### Private Lies, Public Truths

### Biological basis for mimicry

[https://en.m.wikipedia.org/wiki/Mirror_neuron](https://en.m.wikipedia.org/wiki/Mirror_neuron)

### Simulation

Run a quick simulation of Preference Falsification where pairs are selected from a hat to have discussions. First, define population with a two party system. A topic is chosen at random. PersonAttr here are 1) rhetoric (probability of convincing someone) 2) Belief vector for each topic (direction and magnitude). Population belief distributions should start random between [-1.0, 1.0]. Other experiments would be to model a two party system. Or a two party system that is not absolutist

// No preference falsification

```
population = new_population(10000, parties=2)
for timestep in range(n):
    pair = nextpair()
    topic = nexttopic()
    outcome = discuss(pair, topic)
    update(pair, outcome)
```

Here we can understand how polarity affects consensus. Update step has a learning rate and depending on the probability of convincing someone, moves the needle by -1 * lr with p == rhetoric_ability.

```
@dataclass
class Person:
  rhetoric_abilty: float
  beliefs: Dict[str, float]
```

// With preference falsification we need to make it easier for the Sophist to “convince” the other, and a way to quantify “complacency” caused by believing that everyone already believes this or that this person doesn’t need convincing. We need to define some rate of preference falsification for the population or have it be a function of their belief. A relu(0.3) might make sense.

```
@dataclass
class PreferenceFalsifyingPerson:
  rhetoric_abilty: float
  beliefs: Dict[str, float]
  complacency: Dict[str, float]
```
