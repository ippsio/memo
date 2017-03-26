
# Python環境構築

## 前提条件
- CentOS6.8

## pyenvの調達準備
```sh
yum -y install gcc gcc-c++ make git openssl-devel bzip2-devel zlib-devel readline-devel sqlite-devel bzip2 sqlite
```

## pyenvインスコ
```sh
git clone git://github.com/yyuu/pyenv.git ~/.pyenv
```

## .bashrcに追記
```sh
export PYENV_ROOT="${HOME}/.pyenv"
if [ -d "${PYENV_ROOT}" ]; then
    export PATH=${PYENV_ROOT}/bin:$PATH
    eval "\$(pyenv init -)"
fi
```

ちなみに、次のcat～末尾のEOSを全部コピペすれば、.bashrcに追記してくれるよ。
```sh
cat << EOS >> ~/.bashrc

export PYENV_ROOT="${HOME}/.pyenv"
if [ -d "${PYENV_ROOT}" ]; then
    export PATH=${PYENV_ROOT}/bin:$PATH
    eval "\$(pyenv init -)"
fi
EOS
```

## ついでにPyenv-virtualenvを調達
Pyenv-virtualenvがあると、バージョンも環境も簡単にスイッチできるようになる。
```sh
cd ~/.pyenv/plugins
git clone git://github.com/yyuu/pyenv-virtualenv.git
```

## 使いみちの例
### 【汚してもいい環境】と【きれいな環境】を作ってみる。
こういう環境を作ると、
- 【汚してもいい環境】で、パッケージがちゃんとインストールできるか確認。
- ちゃんと入るとわかったパッケージだけを【きれいな環境】にインストール
  - 結果、【きれいな環境】は汚さなくて済む。安全。


#### まずはPythonがないと始まらないので3.5.3をインストール
```sh
pyenv install 3.5.3
```


#### 続いて、【汚してもいい仮想環境】と【きれいな仮想環境】を作ってみる
```sh
$ pyenv virtualenv 3.5.3 beauty3.5.3

  > Requirement already satisfied: setuptools in
  > /root/.pyenv/versions/3.5.3/envs/dirty3.5.3/lib/python3.5/site-packages
  > Requirement already satisfied: pip in
  > /root/.pyenv/versions/3.5.3/envs/dirty3.5.3/lib/python3.5/site-packages

$ pyenv virtualenv 3.5.3 dirty3.5.3

  > Requirement already satisfied: setuptools in
  > /root/.pyenv/versions/3.5.3/envs/dirty3.5.3/lib/python3.5/site-packages
  > Requirement already satisfied: pip in
  > /root/.pyenv/versions/3.5.3/envs/dirty3.5.3/lib/python3.5/site-packages
```

#### それぞれの仮想環境のPythonを使うためのフォルダを作成
```
$ mkdir ~/beauty
$ cd ~/beauty
$ pyenv local beauty3.5.3 # このフォルダでは、【きれいな】pythonが使用される

$ mkdir ~/dirty
$ cd ~/dirty
$ pyenv local dirty3.5.3 # このフォルダでは、【汚してもいい】pythonが使用される
```

こうしておけば、【汚してもいい環境】は、穴があいて擦り切れるまでpip installを試すことができる。
