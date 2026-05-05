<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name: M VARSHINI   </h3>
<h3>Register Number: 212224060293           </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>
<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

# Program:
```
import random
import string

# Fitness Function: Count mismatches
def fitness(current, target):
    score = sum(1 for a, b in zip(current, target) if a != b)
    return score

# Mutate one character in the string
def mutate_string(s):
    index = random.randint(0, len(s) - 1)
    random_char = random.choice(string.ascii_letters)  # A-Z, a-z
    return s[:index] + random_char + s[index + 1:]

# Hill Climbing Algorithm
def hill_climbing(target):
    # Step 1: Generate random string
    current = ''.join(random.choice(string.ascii_letters) for _ in range(len(target)))
    current_fitness = fitness(current, target)

    print("Initial String:", current, "Fitness:", current_fitness)

    iteration = 0

    # Step 4: Loop until global minima (fitness = 0)
    while current_fitness > 0:
        iteration += 1
        
        # Step 2: Mutate a single character
        mutated = mutate_string(current)
        
        # Step 3: Evaluate fitness
        mutated_fitness = fitness(mutated, target)

        # Accept mutation only if it improves fitness
        if mutated_fitness < current_fitness:
            current = mutated
            current_fitness = mutated_fitness
            print(f"Iteration {iteration}: {current}   Fitness: {current_fitness}")

    print("\nTarget string achieved!")
    return current


# ------------------------
# MAIN PROGRAM
# ------------------------

target_string = input("Enter Target String: ")
result = hill_climbing(target_string)

print("Final Output:", result)

```
<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Sample Output:</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>
<hr>
<hr>
<h2>Input and Output</h2>
<h2>String:</h2> HILL CLIMBING
<h2> Output:</h2>
<img width="643" height="509" alt="image" src="https://github.com/user-attachments/assets/c2b6e8f6-7642-42c0-a51f-55a77b3db8ab" />


<h2>Result:</h2>
Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration is implemented.
