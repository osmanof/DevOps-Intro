# Запуск команд

Вывод команды `git log --oneline -1`:

`5ab94e8 (HEAD -> feature/lab2) Add test file`

Вывод команды `git cat-file -p HEAD`:

```
tree b48eab212b16b91c6c96f4bc6d3ddce417216c5b
parent b06ef081730a64a86df0bcff31c42cab5eee03c3
author ocinboca <61325807+osmanof@users.noreply.github.com> 1770923054 +0300
committer ocinboca <61325807+osmanof@users.noreply.github.com> 1770923054 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgLCebBmu+WICygVWASvZtDrknVz
 JEWhK7UOdDwpeNX78AAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
 AAAAQKBSKJmIdbtfNPfgQ+GRJOaY/7sPyigTN4s83WhfAvuh2nhh/fS5a+LO3W2qgtwufv
 /wCPpcZmAjlKjU5WjowAo=
 -----END SSH SIGNATURE-----

Add test file
```

Вывод команды `git cat-file -p b48eab212b16b91c6c96f4bc6d3ddce417216c5b`:

```
100644 blob 6e60bebec0724892a7c82c52183d0a7b467cb6bb	README.md
040000 tree a1061247fd38ef2a568735939f86af7b1000f83c	app
040000 tree 96149242bcc42a03912024494cbdcd21e774baac	labs
040000 tree d3fb3722b7a867a83efde73c57c49b5ab3e62c63	lectures
100644 blob 2eec599a1130d2ff231309bb776d1989b97c6ab2	test.txt
```

Вывод команды `git cat-file -p 2eec599a1130d2ff231309bb776d1989b97c6ab2`: (для примера взял хеш файла `test.txt`)

```
Test content
```

Вывод команды `git cat-file -p 96149242bcc42a03912024494cbdcd21e774baac`: (для примера взял хеш папки `labs`)

```
100644 blob 289342a51812b171c847118da507e49d10faaada	1.jpg
100644 blob 226b581bd0ad91e3dfeadec7981e4f55964337a9	2.jpg
100644 blob b5e42f7a6f3b4d2199c10d848993f1d96fd34593	3.jpg
100644 blob 429a83d2d3f0d09514850d3c24fb95f74bfc2470	4.jpg
100644 blob aa6b7b5c478b439d2c1e9b4f085257782dd68d25	lab1.md
100644 blob cf1ba99be683932b0a1e1cfd84f0d6f0dc0d184f	lab10.md
100644 blob ca6bbf33cb79a950fbf3c517e6b174ac65f5334b	lab11.md
040000 tree 16bf9eb348f7da4acbec0a94fc4a09e46c40064f	lab11
100644 blob fcd2509fd7a30ea3b5cc9e879f97fbb32d3e660d	lab12.md
040000 tree 129069dd8e40511c9ab6c889b375532b1d68fde3	lab12
100644 blob 3128f48b832e6592d02ae82a18f9b89af82c9658	lab2.md
100644 blob 6e453f5c97f02a4bca77db29549154072771ad4a	lab3.md
100644 blob 3aa4439565d04ff637e909ffc164d59a60749239	lab4.md
100644 blob 0435c3fcbd5d21b21cf253af0544a6536247cdb9	lab5.md
100644 blob af90a7fa02f582cd3d31f4d9f71360878f031e92	lab6.md
100644 blob ee11bdfb0d71048268ec439ad0c4ee2f7bf6fd1b	lab7.md
100644 blob 9df09119213b81f88f6b61c89f3bcf223a32ecf6	lab8.md
100644 blob 12e1b875e40d5ef91f11c36fb259f23069fc458f	lab9.md
100644 blob 8595e206039d531f44238a935a933b329c1985ec	submission1.md
```

Вывод команды `git cat-file -p 5ab94e8`: (хеш созданного в начале коммита)

```
tree b48eab212b16b91c6c96f4bc6d3ddce417216c5b
parent b06ef081730a64a86df0bcff31c42cab5eee03c3
author ocinboca <61325807+osmanof@users.noreply.github.com> 1770923054 +0300
committer ocinboca <61325807+osmanof@users.noreply.github.com> 1770923054 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgLCebBmu+WICygVWASvZtDrknVz
 JEWhK7UOdDwpeNX78AAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
 AAAAQKBSKJmIdbtfNPfgQ+GRJOaY/7sPyigTN4s83WhfAvuh2nhh/fS5a+LO3W2qgtwufv
 /wCPpcZmAjlKjU5WjowAo=
 -----END SSH SIGNATURE-----

Add test file
```

## Объяснение

`blob` -- это файл, `tree` -- это директория, `commit` -- это коммит. У каждого есть свой хеш. (если я правильно понял задание)

## Анализ

Судя по выводу, каждому объекту присваивается тип и хеш. Если выполнить `cat-file`, то в консоль напечатается информация, соответствующая типу. Например, для папки выводится список файлов и папок в ней, а для файла -- его содержимое (во всяком случае, с txt файлом так сработало).

## Пример

Ну, пример содержимого файла (blob) есть выше :)

# Resets

## Команды

(не понял вопрос why. Потому что так надо по условию..)

Введенные команды:
`git reset --soft HEAD~1`

`git reset --hard HEAD~1`

`git reflog`

Вывод:
```
bf5ad17 (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
96edaf8 HEAD@{1}: reset: moving to HEAD~1
9bb3aa1 HEAD@{2}: commit: Third commit
96edaf8 HEAD@{3}: commit: Second commit
bf5ad17 (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
5f4f4f4 (origin/git-reset-practice, origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice
5f4f4f4 (origin/git-reset-practice, origin/feature/lab2, feature/lab2) HEAD@{6}: checkout: moving from feature/lab2 to feature/lab2
5f4f4f4 (origin/git-reset-practice, origin/feature/lab2, feature/lab2) HEAD@{7}: pull origin feature/lab2 --rebase (finish): returning to refs/heads/feature/lab2
5f4f4f4 (origin/git-reset-practice, origin/feature/lab2, feature/lab2) HEAD@{8}: pull origin feature/lab2 --rebase (pick): Add test file
```

`git reset --hard bf5ad17`

# Граф

## Команда `git log --oneline --graph --all`

```
* 5b2705f (side-branch) Side branch commit
* bf5ad17 (HEAD -> git-reset-practice) First commit
* 5f4f4f4 (origin/git-reset-practice, origin/feature/lab2, feature/lab2) Add test file
* 51fb75b add information in submission and add images
* ff7a9db add information in submission and add images
* 76de1f0 fill submission file and add screenshots
* 469efd4 docs: add lab1 submission
* b464e36 (origin/main, origin/HEAD, main) add template to main
| * b06ef08 (origin/feature/lab1, feature/lab1) add information in submission and add images
| * 2680529 add information in submission and add images
| * d20d3a9 fill submission file and add screenshots
| * 80339f0 docs: add lab1 submission
|/  
* d6b6a03 (upstream/main, upstream/HEAD) Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
| * 0a09c16 (upstream/release/f25) feat: remove old Exam Exemption Policy
|/  
* 1e1c32b feat: update structure
* 6c27ee7 feat: publish lecs 9 & 10
* 1826c36 feat: update lab7
* 3049f08 feat: publish lec8
* da8f635 feat: introduce all labs and revised structure
* 04b174e feat: publish lab and lec #5
* 67f12f1 feat: publish labs 4&5, revise others
* 82d1989 feat: publish lab3 and lec3
* 3f80c83 feat: publish lec2
* 499f2ba feat: publish lab2
* af0da89 feat: update lab1
* 74a8c27 Publish lab1
* f0485c0 Publish lec1
* 31dd11b Publish README.md
```

## Объяснение

Сверху вниз идут коммиты по времени их создания (последние коммиты идут первыми). Ответвления буквально показывают ветки.

# Теги

```
git tag v1.0.0
git push origin v1.0.0
```

Хеш коммита: `bf5ad171a63df331faf4fa6e18e38ba493be1e21`

## Объяснение

Теги нужны для того чтобы помечать версиями текущие состояния (судя по всему). Во вкладке **Tags** на сайте появляется архив **Source code**, где можно скачать архив с тем состоянием, которое было на момент создания тега. Они важны, чтобы помечать версии релизов.

# git switch vs git checkout vs git restore

## Команды

`git switch vs git checkout vs git restore`

Вывод:
```
Switched to a new branch 'cmd-compare'

```

`git switch -`

```
M	labs/submission2.md
Switched to branch 'git-reset-practice'
Your branch is ahead of 'origin/git-reset-practice' by 1 commit.
  (use "git push" to publish your local commits)
```


`git checkout -b cmd-compare-2`

Вывод:
```
Switched to a new branch 'cmd-compare-2'
```

```
echo "scratch" >> demo.txt
git restore demo.txt
git restore --staged demo.txt
git restore --source=HEAD~1 demo.txt
```

Вывод каждой из последних трех команд:
```
error: pathspec 'demo.txt' did not match any file(s) known to git
```

Причем, если выполнить `git add demo.txt`, то первые две не дают ничего, а последняя даёт такую же ошибку.

## `git status` и `git branch`

`git status`

```
On branch cmd-compare-2
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   labs/submission2.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.DS_Store
	demo.txt
	labs/.DS_Store

no changes added to commit (use "git add" and/or "git commit -a")
```

`git branch`

```
  cmd-compare
* cmd-compare-2
  feature/lab1
  feature/lab2
  git-reset-practice
  main
  side-branch
```


## Объяснение

`git switch` создаёт ветку и переключается на ветку.
`git checkout` позволяет переключаться между ветками, а также восстанавливать файлы из предыдущего коммита (две функции).
`git restore` выполняет функцию восстановления файлов.

По сути `checkout` это `switch` + `restore`.

