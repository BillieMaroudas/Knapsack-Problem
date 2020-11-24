1. Define the problem as a genetic algorithm
We will find the different permutations of the ordering of the boxes that exist in this problem. Every member of the population in each generation is a different permutation of these 7 boxes, meaning there are 7! = 5040 different orderings of the boxes. To find the fitness of a given member of the population, we will add boxes into our backpack in the order they appear in a permutation until we cannot add the next box without going over the 120 weight limit. The cummulative value of the boxes that could be put into the backpack will be the fitness of that inidividual of the population. After each generation, the 50% of the population with the lowest fitness will be culled. Then the remaining members mate and each pair produces 4 offsprings. 

2. Provide the Genome for the algorithm
The genome for each individual is the order of the boxes. To get the initial population, we randomize the order of the boxes 8 times to create 8 separate individual genomes. 

3. Define all the fringe operations
Mutation: For each box in the genome of a member of the population, there is a 5%         chance that it swaps with another random box in the genome. This randomizes the order of the boxes a little in each genome.
Mating: The mating function is demonstrating with the following example. For boxes A,B,C,D,E,F.
                ParentOne:   D , C , A , F , B , E
                ParentTwo:   A , B , C , D , E , F
First we randomly pick a point at which to begin the crossover, lets say the crossover point is at index 4.
                                         0   1   2 , 3 , | 4   5
                  ParentOne:   D , C , E , F , | B , A
                 ParentTwo:   A , B , C , D , | E , F
ParentOne[4] swaps with ParentTwo[4], but that leaves ParentOne with two E's and ParentTwo with two B's. However, we want the genome to contain only one of each box. So we change the B in ParentOne into an E and the original E to a B, and likewise for parentTwo. We do the same for the 5th index of both parents, thus creating two new individuals. We repeat this process to the original parents, but instead of swapping starting after the crossover point, we start at index 0 and go up to         the crossover point. So we have:
                ChildOneA:   D , C , B , A , | E , F
                ChildTwoA:   F , E , C , D , | B , A
        Starting the process from index 0:
                ChildOneB:   F , E , B , A , | C , D
                ChildTwoB:   D , C , E , F , | B , A
These are the final four children from the original parents. This process ensures that no boxes are duplicated or erased in any genome.








