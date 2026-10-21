The Assignment:
"Take a DNA sequence from NCBI (an entire genome) and take 2,000 random samples from the entire sequence of about 100-120 base pairs. Store these samples in an array or a list. Rebuild the DNA sequence using these random samples and find out what will be the main problem with the algorithm approach."

The Answer:
This greedy overlap algorithm fails in the real world because of three major roadblocks. Looking at it from a computer science and biology perspective, here is exactly why the code breaks:
1. The Repeat Trap (The biggest issue)
Genomes are basically long strings full of identical repeating patterns. If the virus has a repeating sequence of 150 characters, but our random reads are only 120 characters long, the algorithm gets completely lost. It’s like trying to put together a jigsaw puzzle of a clear blue sky where all the pieces look exactly the same. The algorithm won't know which branch to take, so it hits a dead end and outputs disconnected fragments (contigs) instead of the full genome.
2. The Missing Data (Coverage Gaps)
Because we extract the reads entirely at random, we aren't guaranteed to cover every single index of the original sequence. Mathematically, random sampling means some spots will just never get picked up unless we pull massive amounts of data (high sequencing coverage). If even a tiny chunk of the original sequence is physically missing from our array, the overlap chain is broken, and the algorithm cannot finish the sequence.
3. The Execution Time (O(N 
2
 ) Complexity)
To find the best matches, this algorithm has to loop through and compare the end of every single read against the beginning of every other read in the pool. For a tiny 2,000-read sample, that’s already millions of string comparisons. If you try to run this nested loop logic on a larger genome with millions of reads, your CPU will essentially lock up. It is terribly inefficient and simply doesn't scale.
