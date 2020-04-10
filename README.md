# Lindel
Lindel is a Logistic regression model to predict insertions and deletions induced by CRISPR/Cas9 editing. 

To use the tool simply type: 

```
git clone https://github.com/shendurelab/Lindel.git 
cd Lindel
python setup.py install
```

Please see full documentation at Lindel webpage.
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


