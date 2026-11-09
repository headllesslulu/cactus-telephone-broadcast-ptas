# cactus-telephone-broadcast-ptas
A (1 + ε) approximation scheme for telephone broadcasting on cactus graphs

Cactus Telephone Broadcast PTAS
How quickly can a message reach an entire network if each informed node can call only one neighbor per round? This project answers that question to any chosen accuracy for cactus graphs, which are networks made of bridges and cycles that meet at junctions. Cycles can be long, and many can meet at the same node.

What the proof guarantees
For any fixed tolerance $0<\varepsilon\leq1$, the algorithm produces a valid schedule in at most $(1+\varepsilon)\mathrm{OPT}$ rounds, where $\mathrm{OPT}$ is the fastest possible broadcast. For example, if the fastest schedule takes 20 rounds, setting $\varepsilon=1/4$ guarantees a schedule of at most 25 rounds.

The theoretical running time is $n^{O(1/\varepsilon^2)}$ with a polynomial-time rational linear programming solver. The bundled Python reference uses exact rational simplex so its decisions can be replayed with exact arithmetic.

How it works
1. Break each cycle into paths. A junction can call one neighbor and let the message travel around the cycle, or call two neighbors and start the two sides separately. Each choice gives the junction one or two call deadlines.
2. Keep tight deadlines exact. Group later deadlines and round the choices to one real plan per cycle. This adds at most four calls to any later deadline group.
3. Use one time budget throughout. Each call and its branch share the same approximation factor. That keeps the same guarantee through the entire network, even when cycles lie several junctions apart.
