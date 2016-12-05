##### このページはCloud9の仮想環境上で、mishima.syk#9ハンズオン環境を作るための資料です。
###### 2016.12.05 kochi

###### カレントの確認
###### /home/uubuntu/workspace
'''bash
   pwd
'''

###### minicondaをDownload
##### Cloud9はHDDが2GBなので、anacondaだと大きすぎる。miniconddaにする。
'''wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh

##### 実行権限付与と、インストール
chmod a+x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh

##### パスを追加( ずっと使う人は.bashrcに追記するのがよい )
export PATH=/home/ubuntu/miniconda3/bin:$PATH

##### 必要なライブラリをインストールする。
##### ただし、HDDが2GBなので、その都度、conda clean --tarball によって ダウンロードしたファイルを 削除する
conda install -y -c conda-forge tensorflow
conda install -y -c conda-forge keras=1.0.7
conda clean —-tarballs
conda install -y -c rdkit rdkit=2016.03.4
conda clean —-tarballs
conda install jupyter matplotlib scikit-learn pandas
conda clean --tarballs
conda clean --index-cache

##### この段階で 123MB 程度残るはず

##### jupyterの設定
##### 面倒なので最低限。ずっと使う人はパスワードを設定しましょう
mkdir jupyter
cd jupyter
# 設定ファイルをつくる。↓のコマンドで
# ~/.jupyter/jupyter_notebook_config.py が生成される
jupyter notebook --generate-config

# ~/.jupyter/jupyter_notebook_config.py を編集する
# ファイルの末尾に↓の4行を追加
c.NotebookApp.ip = "*"
c.NotebookApp.notebook_dir = "/home/ubuntu/workspace/jupyter"
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8080

# jupyterを起動する
jupyter notebook

# ブラウザの別のタブを開き、↓のように開く
# http://(仮想環境名).(アカウント名).c9users.io:8080/
http://mishima9.kochi0603.c9users.io:8080/

# ハンズオン用のデータセットをまるごとダウンロードする
git clone https://github.com/Mishima-syk/9

# おしまい
