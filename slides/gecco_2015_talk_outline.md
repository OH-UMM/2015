# GECCO 2015 talk outline

_It turns out that basic Markdown (including Github Markdown) doesn't support nested lists with different symbol sets (letters, numerals, etc.), so I switched everything to just numerals. It doesn't look super pretty, but it at least does the (auto)numbering correctly. – Nic_

0. Big Picture
    1. Graph DB work suggested we might want to prefer "better" parent as root parent in crossover (show plot from MICS paper?)
    2. We tried that on a bunch of problems
    3. Results are unclear. Definitely improved results for some situations, and in general led to an improvement or no difference. Were some cases, however, where it hurt.

1.   Introduction
    1. Explain Sub-Tree Crossover. _Keep this short since the audience will mostly be quite familiar with these ideas._
        1. Define Root Parent
        2. Define Non-Root Parent
    2. Impact of Crossover Asymmetry on Semantics
        1. Root Parent (Typically) Contributes More Overall Nodes
        2. Nodes Closest to the Root of the Tree (Typically) Have Stronger Impact on Evaluation
        3. We observed in one setting (show MICS plot?) that Fitness of Offspring Tends to Improve When Root Parent Has Better Fitness Than Non-Root Parent
        4. Is this true more generally?
    3. Introduce Crossover Bias

2. Experimental setup
    1. 5 bias values: 0 (no bias), 0.25, 0.5, 0.75, 1 (always bias)
    2. 5 test problems: K Landscapes (K=6), ORDERTREE, U.S. Change, Sine regression, and Pagie-1 regression.
    3. 4 tournament sizes (2, 3, 5, 7), 2 elitisms (0 and 1%), 2 pop sizes (1,024 and 10.240). 100 gens and 100 runs per treatment. _Probably just put Table 1 on a slide._
    3. All done with ECJ. _Do we want to try to submit our implementation of this to ECJ quick so we can say we sent it to them?_ _Say we'll send to ECJ, but not try to do it before GECCO._
    1. Idea of _bias-effective_ and _non-bias-effective_ settings (Fig 2)

3. Results
    2. K Landscapes: It really depends on which part of the elephant you're holding
        1. Overall, adding bias is good: Fig 3
        2. If you focus on bias effective settings, it's awesome: Fig 5
        3. If you split out across tournament sizes, it's mixed (good for 2, maybe bad for 7?): Fig 4
    3. ORDERTREE: Generally helpful: Fig 6
    3. U.S. Change
        1. Across all treatments, nothing much: Fig 7
        2. Focus on successes and bias effective treatments, it's a big win: Fig 9
    4. Pagie-1
        1. Good for binary tournaments, bad for larger tournaments: Fig 10
        2. For bias effective settings, good for binary, neutral elsewhere: Fig 11 _Put these in their own column, making Figure 11 optional in the presentation, but included in the slide deck._
    5. Sine: Good for effective (Fig 12) and flat for non-effective (Fig 13). _Probably try to combine those onto one slide._
    6. Looked at relative differences in parent fitnesses over time (Fig 14). _Maybe make this "optional" depending on time?_

3. Conclusions
     1. Summary
        1. Effects of Crossover Bias Tend to Be Either Beneficial or Neutral (but can occasionally be detrimental)
        1. Crossover Bias is Worth Trying When There is Reason to Suspect Substantial Difference in Parental Fitnesses
           1. Selection Pressure is Weak
           2. Unavoidable Steep Changes in Fitness
           3. Dynamic fitness functions
     2. Further Work
        2. Generalization of Crossover Bias (A.K.A. Crossover Bias May Result in Overfitting)
        3. Examining Other Asymmetries in Evolutionary Systems
            1. Asymmetries are common
                1. Sexual selection in eukaryotes; speciation
                2. Linear GP and stack-based systems
                3. Grammatical evolution
            2. Often not intentional, but more structural side-effects; often understudied
            5. Mention some of the related work, especially the semantic work focusing on _reducing_ the asymmetry between parents and children. Focus is typically on relationship between parents and offspring, though, where we're looking at asymmetries between parents. Other work (e.g., Ryan's "Pygmies and civil servants" and sexual selection) tries to _increase_ the asymmetry between parents, but doesn't then use that to structure the crossover. Gustofsen's work mentioned in the paper.
            1. Better Understand behavior and Performance of Existing Systems
            2. Help in Discovering and Designing New Tools That Leverage These Asymmetries

4. Point to Silico-paleontology blog? _If I actually got that up and running and added a few posts, would we want to have a slide at the end that advertises it? – Nic_ _Probably not going to happen – just don't have time right now._
