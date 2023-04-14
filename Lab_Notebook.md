# Lab Notebook- Sarah Nicholls

ls
# this lists all of the files in my current working directory
# adding -F adds slashes to files you can change directory into
# adding -ltrh gives you ownership info, creation dates, etc

cd nameoffolder
# this changes the working directory
# nameoffolder is argument for cd command

pwd
# this stands for Print Working Directory and shows what directory you're in
# returns embedded folders separated by slashes

# tab can be used to autocomplete words- type first few letters
# hitting tab a lot of times can be used to show what's in a directory

clear
# this will get rid of what's in terminal

ctrl-c
# this will cancel command line & get a new one

.md extension
# this will be v helpful when saving lab notebook/other files from code
# save as, then add this extension
# hashtags will turn different colors/can be used as headers
# top right buttons will let you export as PDF

# command line/"unix" refers to commands

PS1='$ '
# setting a variable to get rid of text on command line

rm directoryname
# removes directory permanently from computer

ssh username@servername.edu
# connects terminal to teaching cluster RON
# ssh san1026@ron.sr.unh.edu

# if problems, open new terminal

file > open workspace from file > emptyworkspace.code.workscape
# this lets us get back into lab notebook each week

mkdir directoryname
# this lets you make a new directory

cp /path to file you're copying/TAB .
# this lets you copy files into directory
# . lets you copy files directly into current directory

# tar file is like zip- compression of other files

tar -xf filename
# this lets tar file be decompressed
# letters are various options of what file does when decompressing
# -xf for decompressing regular tar file

man command
# this opens manual page for desired command
# q lets you quit

# fastq files let you see all sequenced samples
# eg 2 files = 2 sequences

head filename
# this lets you see data in fastq file
# sometimes you also need to include absolute paths if the file isn't already in your working directory, eg head shell_data/.hidden/youfoundit.txt

# each read has info line including sample name, length, etc
# then line of dNTPs
# then line of quality/confidence in dNTPs

command --help
# this gives you list of what command does

# up & down arrows let you view all commands you've done

head -nnumber filename
# this gives you a certain # of lines in file

grep 'sequence' filename | command
# this searches thru file to find something that matches that exact line
# | is called pipe & lets you add another unix command
# eg grep 'SRR097977' SRR097977.fastq | wc

wc
# this gives word count/character count/line count
# adding -l isolates line count

cd ~
# this brings you back to home directory

# relative path: use 1 step to get where you're going

cd /home/users/san1026/gen711/filename/fileaname
# this lets you go via an absolute path
# absolute path: go all the way back to base of computer to get where you're going
# absolute paths ALWAYS start w/ forward slash
# allows you to get directly to a folder w/o even being in the same set of folders

cd ../
# this lets you take a step backwards in folder path, eg going to home from gen711
# cd ../../ lets you take two steps back; adding ../ means adding 1 more step
# adding 2 tabs to end of this lets you see everywhere you can move into

cd ../TAB TAB/filename
# this lets you take relative paths into files
# use as many ../s as needed

EXERCISE 3A: How to get to home directory from untrimmed fastq
1. cd ~
2. cd /home/users/san1026
3. cd ../../../

# Googling is both allowed & encouraged!

ls -a
# this reveals hidden files in a folder

EXERCISE: How to find/open hiden files starting in shell_data
1. ls -a
2. cd .hidden
3. ls
4. head youfoundit.txt

cat filename
# this opens contents of files
# similar to head
# adding strings of file names will open 2 files in a row (first file ends & second begins)
# cat will give you all contents, not just first few like head
# we can use cat to append two files together:
cat firstfile secondfile > newfilename

*
# this will match anything
# anything goes at spot where asterisk is
# eg ls *.fastq will show all fastq files

command > filename.extension
# this redirects command to a separate file
# often use .txt for text files

ls /
# this shows "root", aka all programs available on server
# on ron, "bin" contains all software

EXERCISE 3B: How many programs in /bin...
1. Start w/ letter C: 90
# go into /bin; then ls c* | wc -l
2. Start w/ letter A: 45
3. Start w/ letter O: 22

echo phrase/command
# this will return the phrase
# this can also act as ls, eg echo *fastq will return fastq files

>> filename
# this (append) adds things to existing file
# can be used in conjunction w/ echo: echo phrase >> filename
# above will add phrase to file

> existingfilename
# this will overwrite the file

control-R
# this will open reverse search
# you can search for previous commands you've done by starting to type the command
# hitting control-R again will let you cycle thru all the commands you've done that start w/ same command, eg all your greps

history
# this will print your entire history to your screen

history | grep 'phrase/command'
# this lets you search your history for specific commands

grep -A# -B# 'sequence' filename | wc -l
# this outputs a certain number of lines before + after actual sequence

# when we SSH in, we're automatically dumped into our home directory (san1026, not all the way back at home)

realpath directoryname
# this shows you the absolute path to the given directory

tail filename
# this shows the last few lines in a file

mkdir directory
# this makes a new directory
# have to go stepwise- can't make big long path

mkdir -p directorypath
# this lets you make a long path of folders

curl -O webpagename
# this lets you download files from internet
# ctrl-C lets you cancel

cp /tmp/filename
# this downloads files from TMP server
# use *.extension for all files of a certain type
# add  . to end to copy into current directory

# gz file is compressed like zip

gunzip filename
# this decompresses gz files
# use *.extension.gz to decompress all gz files

ctrl-Z
# this pauses downloads

bg
# this puts processes (eg file decompressions) in background & frees up command line

top
# this shows all programs/processes running on server
# hit q to return to command line; ctrl-C will also get you out
# DO NOT hit keys that aren't q

# fastqs w/ same name & _1 or _2 at end are paired-end reads

less -S filename
# this shows the entirety of each line on a single line
# use arrow keys to navigate
# use q to get out of it

# symbols in quality line instead of letters indicate low quality

# each read has 4 lines: info line, base pairs, +, & quality
# 1:1 matchup between BPs & quality scores

q
# this returns you to command line
# hitting ctrl-C a lot of times will usually also do the same thing if stuck

EXERCISE: Find last read in file
# use tail

EXERCISE: Determine how big files are
1. ls --help
2. find subcommand that allows you to see file size
3. ls --size OR ls -s
4. ls -hs gives this in human-readable format

ls -s
# this lists how big all files in directory are
# paired-end reads should be the same size in megabytes

ls -hs
# this lists how big all files in directory are in human-readable format (MB, GB, etc)

ls -l
# this gives information about files in directory
# ls -lh gives this info in human-readable format

conda activate environmentname
# this inputs you into a new envt, which has various programs installed
# eg conda activate genomics

fastqc -h
# this pulls up the help directory for fastqc program

fastqc filename
# this shows quality of sequences
# can operate on multiple files at once (*)

jobs
# this shows you what's running in background

kill %1
# this cancels first process running in background

mv filename pathname
# this moves file into a different directory
# CARET ISN'T NEEDED!
# can also use this to rename things- mv filename newname.txt

# html files need to be downloaded & opened in web browser to see

unzip filename.zip
# this decompresses zip files

cat */summary.txt
# this shows you all summary information from fastqc files
# can be piped w/ phrases (PASS/FAIl etc)

command ctrl-ENTER
# if you type this into lab notebook, this will shoot it down to terminal & run command

sftp san1026@ron.sr.unh.edu
# this brings you into program that will let you transfer files
# open new terminal for this

get absolutepathway
# sftp command that lets you download a file

ctrl-D
# this exits from server (ssh, sftp, etc)

EXERCISE: determine if images tell anything about quality
1. Per Base N Content- yes; this shows number of uncalled nucleotides
2. Per Base Quality- yes, obviously
3. Per Sequence Quality- yes; this shows the Phred scores per sequence
4. Per Tile Quality- yes, but I don't quite know what it means
5. all others (Adapter Content, Duplication Levels, Per Base Sequence Content, Per Sequence GC content, & Sequence Length Distribution) don't

trimmomatic
# this shows you options to trim data
# PE = paired-ends
# SE = single-ends
# example:
trimmomatic PE -threads 4 SRR_1056_1.fastq SRR_1056_2.fastq  \
    SRR_1056_1.trimmed.fastq.gz SRR_1056_1un.trimmed.fastq.gz \
    SRR_1056_2.trimmed.fastq.gz SRR_1056_2un.trimmed.fastq.gz \
    ILLUMINACLIP:SRR_adapters.fa SLIDINGWINDOW:4:20
# -threads # breaks up file into given # of streams to make things faster
# indented lines are output lines (new fastq files w/ trimmed reads)
# final line indicates adapters that need to be trimmed

\
# this splits up longer commands onto multiple lines

cp /opt/anaconda/anaconda/pkgs/trimmomatic-0.39-1/share/trimmomatic-0.39-1/adapters/NexteraPE-PE.fa .
# this went into program trimmomatic is stored in & copied in adapters that come w/ trimmomatic
# having these in here will trim out all Illumina adapters in files

# example of a for loop
for infile in *_1.fastq.gz 
do
    base=$(basename ${infile} _1.fastq.gz) 
    trimmomatic PE -threads 24 ${infile} ${base}_2.fastq.gz \
        ${base}_1.trim.fastq.gz ${base}_1un.trim.fastq.gz \ 
        ${base}_2.trim.fastq.gz ${base}_2un.trim.fastq.gz \ 
        SLIDINGWINDOW:4:20 MINLEN:25 ILLUMINACLIP:NexteraPE-PE.fa:2:40:15
done

EXERCISE: make new folder & move in trimmed files
1. starting from data, make a folder called trimmed_fastq in data- mkdir trimmed_fastq
2. move all files to trimmed_fastq- cp /tmp/trimmed/*trim.fastq.gz .
3. run fastqc on files- fastqc *trim.fastq.gz

curl -L -o pathway/url
# this lets you download files & save them into specific folder

tar xvf sub.tar.gz
# this decompresses tar files

conda env list
# this shows all possible conda environments

bwa
# this is in genomics-plus & lets you align things

bwa index pathwayname/filename
# this speeds up computation of file

ls -lthr pathwayname
# this shows files in chronological order

bwa mem referencegenome forwardread reverseread
# this aligns reads to reference genome

> pathwayname/filename.aligned.sam
# run this at end of command 360 to move aligned reads into new SAM file

grep -v 'sequence' pathway/foldername
# "inverse grep"; excludes lines w/ matches to sequence
# '^sequence' will only remove lines w/ sequence at start of line

samtools
# this program lets you manipulate alignment files

samtools view -S -b pathway/filename.sam > pathway/filename.bam
# this compresses SAM file to BAM file

samtools sort -o pathwayname/filename.aligned.sorted.bam pathwayname/originalfilename.bam
# this sorts BAM file into new sorted file

samtools flagstat pathwayname/filename.sorted.bam
# this gives quality of sorted BAM file
# shows PCR duplicates, how many paired to sequencing, etc.

bcftools mpileup -Ob -o pathwayname/filename.bcf -f pathway/referencegenome pathway/BAMfile
# this looks for genetic variation (eg SNPs) in BAM file compared to reference genome
# adding & lets it run in background

jobs
# this lets you see jobs running on terminal

disown -h
# this lets you keep running jobs on server even if you log off

bcftools view pathway/filename.bcf | head
# this shows bcf file in readable format

# remember to conda into genomics-plus before variant calling!

samtools tvew pathway/filename.bam pathway/referencegenome
# this is a simple alignment viewer

ctrl-D
# this disconnects from sftp file

get absolutepathway/filename
# this fetches files in sftp 
# use * to get all files associated w/ that file

EXERCISE: Download the reference genome (ecoli_rel606.fasta), .bams, .bai, and .vcf to your desktop into a ‘files_for_igv’ folder with sftp. Bonus for doing it all on command line.

HOW TO MAKE NEW DESKTOP FOLDER:
1. mkdir ~Desktop/foldername
2. cd ~/Desktop/foldername

HOW TO DOWNLOAD TO DESKTOP:
1. Change directories into desired desktop folder
2. sftp san1026@ron.sr.unh.edu
3. Enter password
4. get absolutepathway/referencegenome*
5. get absolutepathway/BAMfile* (aligned.sorted)
6. get absolutepathway/VCFfile* (final_variants)

HOW TO VIEW ON IGV:
1. Open FASTA & FAI of reference simultaneously on igv.org (genome > local file)
2. Open BAM & BAI simultaneously as tracks (tracks > local file)
3. Zoom in

![plot](url)
# this is used to put images into GitHub

git clone githuburl
# this pulls GitHub repository into directory
# make sure you're not ssh'ed in!

HOW TO MAKE A REPO ON GIT:
1. go to "repositories"
2. click "new repository"
3. add a README file
4. choose a template/license
5. 

github.com/jthmiller/gen711-811-example
# this is the example repo w/ the project rubric in

use pull requests to sync data- non-host has to open it