# Git

Git sistema distribuído de controle de versão que cria um repositório sobre um diretório do sistema operacional. Disponível p/ [Windows](https://git-scm.com/downloads), Linux e Mac.
## Acessar o Git
  - Abrir o prompt do Git (ctrl + ' chama o terminal no VS-Code)
  - Testar a versão do Git
  - Acessar a pasta desejada via prompt.
```
git --version
cd pasta\projeto
```
  
## Fluxo 1: configuração do local p/ o remoto (geralmente online)
*git init* cria um subdiretório chamado **.git** e gera a seguinte configuração inicial no arquivo **.git\config**
```
git init
```
>[core]  
>	repositoryformatversion = 0  
>	filemode = false  
>	bare = false  
>	logallrefupdates = true  
>	symlinks = false  
>	ignorecase = true  
	
*git remote add origin* configura o apontamento do servidor remoto e complementa a configuração no arquivo **.git\config**
```
git remote add origin https://github.com/dj79/git-windows.git
```
>[remote "origin"]  
>	url = https://github.com/dj79/git-windows.git  
>	fetch = +refs/heads/\*:refs/remotes/origin/\*

*git config branch.master.remote* relaciona o branch local com o branch remoto e complementa a arquivo **.git\config**
```
git config branch.master.remote origin
```
>[branch "master"]
	remote = origin
	
*git config branch.master.merge* complementa a seção branch master do arquivo **.git\config**
```
git config branch.master.merge refs/heads/master
```
>[branch "master"]
	remote = origin
	merge = refs/heads/master
	
## Fluxo alternativo 1 configuração do remoto p/ o local
*git clone* realiza todos os passos do fluxo 1 e faz o download (git pull) de um repositório remoto p/ uma pasta local
```
git clone https://github.com/dj79/git-windows.git
```
## Fluxo 2 organização
Após o Git estar devidamente configurado e o momento de manipular o projeto que esta agora sobre o monitoramento do Git. Executar o comando para pegar a última versão (pull - GetLatestVersion)
```
git pull
```
*git status* apresenta uma série de informações sobre o branch, nem todas visíveis inicialmente:
verifica o estado do branch esta intacto ainda (up-to-date)
lista de arquivos Untracked (não monitorados pelo Git ainda, ou seja unstage)  
lista de arquivos Changes to be committed (situação staging que forão alterados)
verifica se há diferença entre o branch e o origin/master, com quant. de commit a mais e sugestão de git push.
```
git status
```

*git add* inicia monitoramento sobre os arqs em situação untracked do projeto, os arquivos ficarão em situação staging
```
git add arq1.html arq2.css arq3.js
git add *
```

*git commit -m* organizar arquivos editados em situação staging e preencher um comentário, 
este comando senão existe pendencias de pull e arquivos pendentes de commit
```
git commit -m 'primeiro commit'
```	

*git log* histórico de commits no branch
```
git log
```

*git push* envia os arquivo par ao repositório remoto
```
git push
```