# Using Jupyter Notebooks

You will need start a conda environment with the following in your cli

```
conda init
conda create --name cloudstor
```

activate it and install cloudstor + any other libraries that are required with - 

```
conda activate cloudstor
pip install numpy
pip install cloudstor
pip install (library required)
```

Now add it to Jupyter notebook with the following commands

```
conda install -c anaconda ipykernel
python -m ipykernel install --user --name=cloudstor
```

Activate a Juptyer notebook and when selecting new file, instead of choosing Python3 choose the cloudstor kernel

To see a list of files then access private files follow this example, password is the app password created above.
```
from cloudstor import cloudstor

private_file = cloudstor(private=True, username="bollands.c@wehi.edu.au", password="*************")

private_file.list('test/')

['mydata.csv', 'test.csv', 'test_two.csv']

with private_file.open("test/test.csv") as f:

    a = f.read()

print(a)

```
To access a file that has been shared to you privately with a cloudstor link and password.

```
public_file = cloudstor(url="https://cloudstor.aarnet.edu.au/plus/s/rkXY4IcMEBsJScp", password='********)

with private_file.open("mydata1.csv") as f:

    b = f.read()

print(b)
```
