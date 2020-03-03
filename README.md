# electron_id

The steps that you have to follow each time to run an ipynb file at beluga cluster:

1) ssh -Y username@beluga.computecanada.ca
2) module load python/3.6
3) source $HOME/jupyter_py3/bin/activate
4) salloc --time=1:0:0 --account=rpp-bengioy --gres=gpu:1 --cpus-per-task=8 --mem=64G  srun $VIRTUAL_ENV/bin/notebook.sh

At step 4 one can choose as many gpus up to 4 and choose memory up to 186GB
also 3 hr allocation time for the gpu with time=3:0:0 although you have to wait longer.
If you are not going to use a gpu then the access is faster and the command is:

salloc --time=1:0:0 --ntasks=1 --cpus-per-task=8 --mem-per-cpu=128M --account=def-bengioy srun $VIRTUAL_ENV/bin/notebook.sh


5) sshuttle --dns -Nr username@beluga.computecanada.ca


with this step you create a tunnel so that you can copy and paste the link to the 
interactive notebook. As an example:

After step 4 you are given a token something like
http://blg4101.int.ets1.calculquebec.ca:8888/?token=3ecba362576958a8cd7205dae93645b12b1


After creating tunnel you are free to copy paste this link & work on Jupyter Notebook

You need to follow these steps every time you want to run the code. But beware that before taking any of these steps one has to download the install the jupyter notebook and create a python virtual environment. All detailed information can be found at:

https://docs.computecanada.ca/wiki/Jupyter

