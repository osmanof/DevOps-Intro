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


