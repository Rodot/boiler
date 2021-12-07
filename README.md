# Boiler

Install chocolatey for software management automation on windows

``` cmd
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

choco feature enable -n allowGlobalConfirmation
```

Install required softwares using chocolatey

``` cmd
choco install miniconda3 --params="'/AddToPath:1'"
choco install vscode

choco install git
choco install github-desktop

choco install vcredist140
choco install vcredist2010
choco install vcredist2013
choco install vcredist2017
```

Add vs code extensions

``` cmd
code --install-extension ms-python.python
code --install-extension mechatroner.rainbow-csv
code --install-extension DavidAnson.vscode-markdownlint
```

Setup python conda environement

``` cmd
activate.bat
conda update conda --yes
conda update conda-build --yes
conda create --name boiler python=3.8 --yes
conda activate boiler
pip install -r requirements-frozen.txt
```

Update everything

``` cmd
choco upgrade chocolatey
choco upgrade all

activate.bat boiler
conda update conda --yes
conda update conda-build --yes
pip install -r requirements.txt --upgrade
pip freeze > requirements-frozen.txt
```
