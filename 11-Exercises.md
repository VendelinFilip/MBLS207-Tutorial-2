
## Page 33

11. Exercises

11.1. Extract the files for the exercises
Download the file exercise_files.tar.gz from Blackboard. This is a zipped tape archive (tar). To extract its contents use the following command:
$ tar -xzvf exercise_files.tar.gz
Delete the original tar after you have checked if the extraction worked.

11.2. Order in the chaos
In the Chaos directory you will see multiple different files, which upon inspecting the extensions have very different content. Actually, these files do not have any content at all (check with `ls -l Chaos`).

a. Let's first do some ordering: make with a single command four new directories in the tutorial2_files folder, named Text, Pictures, Music and Sequences.
b. Move the files in Chaos to the correct new directory, based on their file extensions.
c. Remove the Chaos directory.
d. Change the extension of the picture files from jpeg to jpg.
e. The files logfile.txt and genome.fa are very important and therefore a backup is needed. Copy these files to the Backup directory.
f. Imagine the music files were corrupted and that's why you want to get rid of them. Remove the Music directory and its content.

11.3. Sequence files
The genome of a novel bacterial species named *Candidatus Moanabacter tarae* was successfully reconstructed from a marine metagenome (Vosseberg et al., MRA, 2018). The genome file and the file containing the predicted proteins are called moanabacter_tarae_genome.fa and moanabacter_tarae_proteins.fa, respectively.

a. Open the genome file with less and look at the structure of this file. Search for the pattern ATGTGA (start + stop codon) and go through a couple of hits.
b. Use grep to find the number of lines in which this pattern occurs. Is this also the total number of times this pattern occurs in the file?
c. Which lines start with a start codon and end with a stop codon? Could these lines be open reading frames?
d. Which of the lines of (c) also has three consecutive AG dinucleotides in the middle?
e. Open the file in less again and search for the following patterns to ensure you understand what . and * are doing: A...T, AG*T and A*C*G*T*.
f. Which of the following four patterns will generate the most matches in the file: ACGT, AC.GT, AC*GT or AC.*GT? Which pattern will be most affected if the entire sequence would be on a single line?
g. Open the predicted proteins file in less and look at its structure. How many predicted proteins are there?
h. Think of a short word only consisting of letters that are valid amino acids and check if you can find that word in a protein.
i. How many non-ribosomal proteins are there?

&lt;page_number&gt;33&lt;/page_number&gt;

---


## Page 34

11.4. Binary and text files
a. Open the file tbb.xlsx with less. You will get a warning that the file may be a binary file (which it is). Although most of the file is gibberish, you can see some structure. Actually, Excel (and also Word, PowerPoint, etc.) files are archives. You can see the contents with the following command:
```bash
$ unzip -l tbb.xlsx
```
If unzip is not installed, you can install it yourself with the following command (you will need to fill in your password):
```bash
$ sudo apt install unzip
```
b. The sheet with the information was saved as a tab-separated file on a Mac (tbb_cr.tsv). This results in the newline characters being carriage returns (\r). How are these characters depicted in less?
c. Use the safest Unix plain text file (tbb.tsv) for the following task: extract the people with a PhD (dr. title) and redirect their lines to a new file.

&lt;page_number&gt;34&lt;/page_number&gt;
