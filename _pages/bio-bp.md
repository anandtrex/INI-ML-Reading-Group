---
layout: page
title: Biologically plausible backpropagation
description: and backpropagation through time
permalink: /bio-bp/
---

<!--
INSTRUCTIONS TO ADD REFERENCES:
Add references to `bio-bp.bib` file in the root directory in bibtex format and cite here using `{% cite refkey --file bio-bp %}`
-->

# Some overview resources
- A discussion of the problem on [psychology.stackexchange](https://psychology.stackexchange.com/questions/16269/is-back-prop-biologically-plausible)
- Very opinionated and narrow survey papers: {% cite lillicrap_Backpropagation_2019 lillicrap_Backpropagation_2020  --file bio-bp %}.

# Main problems:

❶ Weight transport problem, synaptic symmetry

❷ Backward pass, memory

❸ Correspondence to actual neural circuitry

❹ Online learning, Catastrophic forgetting etc.

# Solutions

## Papers that solve ❶ but not ❷
- Random feedback alignment {% cite lillicrap_Random_2016 --file bio-bp %} solves ❶ layer-wise, 
- Direct feedback alignment (DFA) {% cite nokland_Direct_2016 --file bio-bp %} is layer agnostic, broadcasts errors to all layers.
- Broadcast alignment (BA) {% cite samadi_Deep_2017 --file bio-bp %} broadcasts errors to all layers, essentially same as DFA.

## Papers that solve ❷ but not ❶
- For recurrent networks, BPTT can be implemented as forward-mode differentiation, called RTRL {% cite williams_Learning_1989 --file bio-bp %}
- Truncated BPTT can be approximated with SnAp>2 {% cite menick_Practical_2020 --file bio-bp %}
- Nice overview of various approximations to BPTT, biologically plausible and otherwise {% cite marschall_Unified_2019 --file bio-bp %}

## Papers that solve ❶ and ❷
- Local approximations of RTRL + DFA: 
    - RFLO  {% cite murray_Local_2019 --file bio-bp %} for sigmoidal RNNs.
    - e-prop  {% cite bellec_solution_2020 --file bio-bp %} is a more general formulation but applied to spiking neurons.
    - SnAp-1 is equivalent to e-prop without DFA {% cite menick_Practical_2020 --file bio-bp %}.
- Synthetic gradients {% cite jaderberg_Decoupled_2016 --file bio-bp %} learns separate networks to predict feedback signals.

# Others
- Target propagation {% cite bengio2014auto bengio_Early_2015 scellier_Biologically_2016 --file bio-bp %} but see {% cite meulemans2020theoretical --file bio-bp %}
- Difference target propagation {% cite lee2015difference --file bio-bp %}
- Equilibrium propagation {% cite scellier_Equilibrium_2017 scellier_Equivalence_2018 --file bio-bp %}
- Latent equilibrium {% cite haider2021latent --file bio-bp %}
- Using dendrites to propagate errors {% cite sacramento_Dendritic_2018 guerguiev2017towards --file bio-bp %} but require specific circuit motifs.
- Predictive coding networks do exact backprop {% cite song2020can --file bio-bp %}
- Fixed weight RNNs can learn (but may not be BP)  {% cite cotter_Fixedweight_1990 hochreiter_Learning_2001 --file bio-bp %}
- Can meta-learn backprop {% cite kirsch2021meta --file bio-bp %}

# References

{% bibliography --file bio-bp --cited %}
