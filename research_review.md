# Research Review

The paper describes three important historical developments in the field of AI planning and search. It takes a deeper look into the classical planning problem(fully observable, deterministic, static, finite and discrete environments[2]) description languages.

## STRIPS (Stanford Research Institute Problem Solver)

STRIPS was first developed as an automated planner[1]. Later the same name was adopted as the reference to the formal language which describes the input the the initial STRIPS automated planner. The introduction of STRIPS as a formal language is especially important as it laid the ground for the upcoming development of automated planning problems descriptions. STRIPS only allows positive literals, closed world assumptions, one-way effects, ground literals in goals, goals/effects as conjunctions[2].

## ADL (Action Description Language)

Action Description Language was developed in particular for robots by Edwin Pednault[3]. It builds up on STRIPS. In particular it allows for negative literals, open world assumptions, two-way effects, quantified variables in goals, disjunctions in goals, conditional effects, use of equality predicate, variable types[2].

## PDDL (Planning Domain Definition Language)

PDDL was introduced as a standarisation of formal languages syntax. It is computer parsable and encapsulates sublanguages such for STRIPS or ADL as well as a hierarchical task network[2]. PDDL was developed for the planning competitions at the AIPS conference in 1998. It's composed of definitions for such elements as initial state, predicates, objects, goal states, actions and operators[4].

# References

0. Richard E. Fikes, Nils J. Nilsson (1971). ["STRIPS: A New Approach to the Application of Theorem Proving to Problem Solving"](http://ai.stanford.edu/~nilsson/OnlinePubs-Nils/PublishedPapers/strips.pdf)
0. Stuart J. Russell, Peter Norvig (2003). ["Artificial Intelligence: A Modern Approach"](http://aima.cs.berkeley.edu/)
0. Edwin Pednault (1987). ["Formulating Multiagent, Dynamic-World Problems in the Classical Planning Framework"](https://books.google.pl/books?id=WjAw8zHbeegC&pg=PA49&lpg=PA49) in "Reasoning about actions and plans"
0. Drew McDermott, Malik Ghallab, Adele Howe, Craig Knoblock, Ashwin Ram, Manuela Veloso, Daniel Weld, David Wilkins (1998). ["PDDL - The Planning Domain Definition Language"](http://icaps-conference.org/ipc2008/deterministic/data/mcdermott-et-al-tr-1998.pdf)
0. Michael Gelfond, Vladimir Lifschitz (1998) ["Action Languages"](http://www.ep.liu.se/ea/cis/1998/016/)
