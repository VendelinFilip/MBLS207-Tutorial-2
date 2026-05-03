# 11. Exercises

## 11.1. Extract the files for the exercises

Download the file `exercise_files.tar.gz` from Blackboard. This is a zipped tape archive (tar). To extract its contents use the following command:

```bash
$ tar -xzvf exercise_files.tar.gz
```

Delete the original tar after you have checked if the extraction worked.

## 11.2. Order in the chaos
In the `Chaos` directory you will see multiple different files, which upon inspecting the extensions have very different content. Actually, these files do not have any content at all (check with `ls -l Chaos`).

<ol type="a">
  <li>Let's first do some ordering: make with a single command four new directories in the <code>tutorial2_files</code> folder, named <code>Text</code>, <code>Pictures</code>, <code>Music</code> and <code>Sequences</code>.</li>
  <li>Move the files in <code>Chaos</code> to the correct new directory, based on their file extensions.</li>
  <li>Remove the <code>Chaos</code> directory.</li>
  <li>Change the extension of the picture files from <code>jpeg</code> to <code>jpg</code>.</li>
  <li>The files <code>logfile.txt</code> and <code>genome.fa</code> are very important and therefore a backup is needed. Copy these files to the <code>Backup</code> directory.</li>
  <li>Imagine the music files were corrupted and that's why you want to get rid of them. Remove the <code>Music</code> directory and its content.</li>
</ol>

## 11.3. Sequence files

The genome of a novel bacterial species named *Candidatus Moanabacter tarae* was successfully reconstructed from a marine metagenome (Vosseberg *et al.*, MRA, 2018). The genome file and the file containing the predicted proteins are called `moanabacter_tarae_genome.fa` and `moanabacter_tarae_proteins.fa`, respectively.

<ol type="a">
  <li>Open the genome file with <code>less</code> and look at the structure of this file. Search for the pattern <code>ATGTGA</code> (start + stop codon) and go through a couple of hits.</li>
  <li>Use <code>grep</code> to find the number of lines in which this pattern occurs. Is this also the total number of times this pattern occurs in the file?</li>
  <li>Which lines start with a start codon and end with a stop codon? Could these lines be open reading frames?</li>
  <li>Which of the lines of (c) also has three consecutive AG dinucleotides in the middle?</li>
  <li>Open the file in <code>less</code> again and search for the following patterns to ensure you understand what <code>.</code> and <code>*</code> are doing: <code>A...T</code>, <code>AG*T</code> and <code>A*C*G*T*</code>.</li>
  <li>Which of the following four patterns will generate the most matches in the file: <code>ACGT</code>, <code>AC.GT</code>, <code>AC*GT</code> or <code>AC.*GT</code>? Which pattern will be most affected if the entire sequence were on a single line?</li>
  <li>Open the predicted proteins file in <code>less</code> and look at its structure. How many predicted proteins are there?</li>
  <li>Think of a short word only consisting of letters that are valid amino acids and check if you can find that word in a protein.</li>
  <li>How many non-ribosomal proteins are there?</li>
</ol> 

## 11.4. Binary and text files

a. Open the file `tbb.xlsx` with `less`. You will get a warning that the file may be a binary file (which it is). Although most of the file is gibberish, you can see some structure. Actually, Excel (and also Word, PowerPoint, etc.) files are archives. You can see the contents with the following command:

```bash
$ unzip -l tbb.xlsx
```

If `unzip` is not installed, you can install it yourself with the following command (you will need to fill in your password):

```bash
$ sudo apt install unzip
```

b. The sheet with the information was saved as a tab-separated file on a Mac (`tbb_cr.tsv`). This results in the newline characters being carriage returns (`\r`). How are these characters depicted in `less`?

c. Use the safest Unix plain text file (`tbb.tsv`) for the following task: extract the people with a PhD (dr. title) and redirect their lines to a new file.
