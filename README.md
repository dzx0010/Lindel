# Lindel
Lindel is a Logistic regression model to predict insertions and deletions induced by CRISPR/Cas9 editing. 

How to run?
1.	Set up running environment and install software:
(1)	Modify shebang line of setup.py to make it run correctly
(2)	$Python3 setup.py build    to build environment 
(3)	$python3 setup.py install  to install software needed
(4)	$python3 setup.py - - help  can help you run  

#1.need install numpy and spicy packages before run
python3 setup.py build
python3 setup.py install

# if not install successfully
you can try pip install
# Run the below from within your $HOME directory on the ASC!!

# Use python3 to install pip (a python package/library manager) in your user account \
# using a python script copied from the biobootcamp directory

cp ~/biobootcamp/get-pip.py . && python3 get-pip.py --user

# Confirm that pip is running in your user account and its version is 20.0.2

.local/bin/pip --version

# Now we need to add the ~/.local/bin to our $PATH, so....

nano ~/.bashrc.local

# And add the following to the bottom of the file (what's the reason for the below?)

export PATH=~/.local/bin:$PATH

# Now log out and back into your ASC account to pick up the new $PATH. To make sure this is the case,

echo $PATH

# And be sure the new ~/.local/bin is at the beginning of your $PATH

# Now time to use pip to install matlibplot

pip install spicy


2.	Predict the mutational outcomes
$ python3 Lindel_prediction.py [argument1 argument2]
Argument 1 is local sequence context which has PAM region (NGG) at 34~36bp. SgRNA should be from 14 to 33 bp of sequence.
Argument 2 is output filename.
For example:
One of my project is knocking out MC4R gene which is associated with dominantly inherited obesity using CRISPR/Cas9 to get fast growth channel catfish. SgRNA is designed using CRISPRscan tools at MC4R exon1: CCGCCTGCCACACGGGGCCGTTCCCCGGTAAGGCGGCGATGCGTTTCATGTGAA
I used Lindel to predict the mutational outcomes to check if the SgRNA is a efficient one.
$ python3 Lindel_prediction.py CCGCCTGCCACACGGGGCCGTTCCCCGGTAAGGCGGCGATGCGTTTCATGTGAAGCCGCGCCAAGAGGAACATGTGCACGTAAAGCGAGGCCA output
It will output a file named output_fs_0.818.txt
Results as follows:
CCGCCTGCCACACGGGGCCGTTCCCCGGTA | AGGCGGCGATGCGTTTCATGTGAA0	
CCGCCTGCCACACGGGGCCGTTCCCCGGTA | -GGCGGCGATGCGTTTCATGTGAA 10.71271172	D1  0
CCGCCTGCCACACGGGGCCGTTCCCCGG-- | ---CGGCGATGCGTTTCATGTGAA 5.01879496 D5  -2
CCGCCTGCCACACGGGGCCGTTCCCCGGTA A AGGCGGCGATGCGTTTCATGTGAA 4.50490689 I1+A
CCGCCTGCCACACGGGGC------------ | ----GGCGATGCGTTTCATGTGAA 3.09079637 D16 -12
CCGCCTGCCACACGGGGCCGTTC------- | ------------GTTTCATGTGAA 2.78325119 D19  -7
CCGCCTGCCACACGGGGCCGTTCCCCGG-- | ------CGATGCGTTTCATGTGAA 2.50422540 D8  -2
CCGCCTGCCACACGGGGCCGTTCCCCGGT- | -------GATGCGTTTCATGTGAA 1.90758451 D8  -1
CCGCCTGCCACACGGGGC------------ | -------GATGCGTTTCATGTGAA 1.81548470 D19  -12
CCGCCTGCCACACGGGGCCGTTCCCCGG-- | AGGCGGCGATGCGTTTCATGTGAA 1.75673152 D2  -2
…



