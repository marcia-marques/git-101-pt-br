# Índice

[Criando um projeto](#criando-um-projeto) <br>
[Usando branches](#usando-branches) <br>

Esse tutorial foi criado no sistema operacional **_Linux_**. Alguns comandos podem ser diferentes se você estiver utilizando _Windows_ ou _Mac_.

# Criando um projeto
[&uarr;](#índice)

1 - Criar um projeto no seu computador e iniciar o controle de versão

```
mkdir mastering-git-branches
cd mastering-git-branches
git init
```

2 - Criar um repositório no `Github`

![image](https://user-images.githubusercontent.com/75334161/120942426-33072b00-c6ff-11eb-938d-2e5b2e341cef.png)

IMPORTANTE: Não crie nenhum arquivo ao iniciar o repositório (Readme ou License)

3 - Criar uma conexão entre o repositório local (projeto no seu computador) e o repositório remoto (`Github`)

```
git remote add origin https://github.com/marcia-marques/mastering-git-branches.git
```

Para listar todas as coexões `git remote -v`:

```
marcia@nt-marcia:~/mastering-git-branches$ git remote -v
origin	https://github.com/marcia-marques/mastering-git-branches.git (fetch)
origin	https://github.com/marcia-marques/mastering-git-branches.git (push)
```

4 - Vamos criar um arquivo txt para usar como exemplo e enviar as modificações para o repositório remoto

```
vim log.txt
```

O comando `git status` mostra quais foram as alterações feitas:

```
marcia@nt-marcia:~/mastering-git-branches$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	log.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Use o comando `git add` para selecionar os arquivos modificados:

```
marcia@nt-marcia:~/mastering-git-branches$ git add log.txt 
marcia@nt-marcia:~/mastering-git-branches$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   log.txt
```

Faça o `commit` das modificações:

```
marcia@nt-marcia:~/mastering-git-branches$ git commit -m "Initial commit"
[master (root-commit) fd86d22] Initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 log.txt
```

Finalmente, envie as modificações para o repositório remoto com o comando `git push origin master`

```
marcia@nt-marcia:~/mastering-git-branches$ git push origin master
Username for 'https://github.com': marcia-marques	
Password for 'https://marcia-marques@github.com': 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 216 bytes | 216.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/marcia-marques/mastering-git-branches.git
 * [new branch]      master -> master
```

Repare que `master` é o nome do `branch`:

![image](https://user-images.githubusercontent.com/75334161/120944149-53d47e00-c709-11eb-8c58-0c0b1dad97ad.png)

O Github usa como padrão `main`, mas quando conectamos o nosso repositório ele fez a modificação automaticamente. Também é possível mudar o nome do branch posteriormente.

# Usando branches
[&uarr;](#índice)

Vamos utilizar os `branches` para fazer diferentes modificações

```
marcia@nt-marcia:~/mastering-git-branches$ git branch list
marcia@nt-marcia:~/mastering-git-branches$ git branch
  list
* master
marcia@nt-marcia:~/mastering-git-branches$ git checkout list
Switched to branch 'list'
marcia@nt-marcia:~/mastering-git-branches$ git branch
* list
  master
```

Após fazer as alterações, fazemos o `commit`, voltamos para o `master`, fazemos o `merge` e deletamos o `branch`

```
marcia@nt-marcia:~/mastering-git-branches$ git commit -m "add items"
[list 66bd6bc] add items
 1 file changed, 4 insertions(+)
marcia@nt-marcia:~/mastering-git-branches$ git checkout master
Switched to branch 'master'
marcia@nt-marcia:~/mastering-git-branches$ git branch
  list
* master
marcia@nt-marcia:~/mastering-git-branches$ git merge list
Updating 73022ba..66bd6bc
Fast-forward
 log.txt | 4 ++++
 1 file changed, 4 insertions(+)
marcia@nt-marcia:~/mastering-git-branches$ git branch -d list
Deleted branch list (was 66bd6bc).
```

![image](https://user-images.githubusercontent.com/75334161/121055198-6f846680-c793-11eb-853e-ded4409afaa9.png)

