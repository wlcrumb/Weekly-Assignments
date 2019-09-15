
#This series of commands allows a user to single out one fasta from WA1.fasta and write it to a separate file for easier use.
#Input: A .fasta file which contains multiple fasta entries.
#Output: A .fasta file which contains the single desired entry.

# The first pipline ensures that base file is in the current directory and provides its total number of lines and a preview of the file.
find WA1.fasta | wc -l WA1.fasta | head WA1.fasta

# The second pipeline determines the line numbers which correspond to the myoglobin entry for red kangaroos, and then writes those lines
# into a new fasta file.
var1=$(grep -n "red kangaroo" Sample.txt | grep -Eo '^[^:]+') | var2=$((var1+1)) | sed "$var1,$var2 w red_kangaroo.fasta" WA1.fasta

# The final pipeline finds the file in the current directory and opens it with less.
find red_kangaroo.fasta | less red_kangaroo.fasta
