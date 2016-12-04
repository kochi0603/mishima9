# mishima9
pwd
# /home/uubuntu/workspace

wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh

chmod a+x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh

export PATH=/home/ubuntu/miniconda3/bin:$PATH

conda install -y -c conda-forge tensorflow
conda install -y -c conda-forge keras=1.0.7
conda clean —-tarballs
conda install -y -c rdkit rdkit=2016.03.4
conda clean —-tarballs
conda install jupyter matplotlib scikit-learn pandas
conda clean --tarballs
conda clean --index-cache

# 123MB 残る


mkdir jupyter
cd jupyter
jupyter notebook --generate-config
#>>> Writing default config to: /home/ubuntu/.jupyter/jupyter_notebook_config.py
python -c "from notebook.auth import passwd;print(passwd())"
#>>> Enter password: #Jupyterのアクセス時に使うパスワードを入力する
#>>> Verify password:
#>>> 'sha1:......' #sha以降をコピーしておく

echo 'c.NotebookApp.ip = "*"'             >> ~/.jupyter/jupyter_notebook_config.py
echo 'c.NotebookApp.notebook_dir = "/home/ubuntu/workspace/jupyter"' >> ~/.jupyter/jupyter_notebook_config.py
echo 'c.NotebookApp.open_browser = False' >> ~/.jupyter/jupyter_notebook_config.py
echo 'c.NotebookApp.port = 8080'          >> ~/.jupyter/jupyter_notebook_config.py
#echo 'c.NotebookApp.kernel_spec_manager_class = "environment_kernels.EnvironmentKernelSpecManager"' >> ~/.jupyter/jupyter_notebook_config.py
#echo 'c.EnvironmentKernelSpecManager.env_dirs=["/home/ubuntu/workspace/.pyenv/versions/miniconda3-4.0.5/envs"]' >> ~/.jupyter/jupyter_notebook_config.py


http://mishima9.kochi0603.c9users.io:8080/

git clone https://github.com/Mishima-syk/9/tree/master/iwatobipen
