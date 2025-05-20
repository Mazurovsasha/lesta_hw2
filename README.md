# Домашняя работа к лекции №2 Мазуров А.

## 1. Создайте локальный Git-репозиторий.

```bash
git init
```
## 2. Настройте имя пользователя и email для текущего репозитория.

```bash
git config user.name "Alex Mazurov"
git config user.email "mazurovsasha@gmail.com"
git config --list --local
```
➜  HW2_Lesta git:(master) ✗ git config --list --local
```
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
user.name=Alex Mazurov
user.email=mazurovsasha@gmail.com
(END)
```

## 3. Создайте структуру проекта с несколькими директориями. Добавьте не менее трёх файлов в разные каталоги.

```bash
mkdir 1
echo "Dir 1" > /home/sasha/HW2_Lesta/1/1.txt
mkdir 2
echo "Dir 2" > /home/sasha/HW2_Lesta/2/2.txt
mkdir 3
echo "Dir 3" > /home/sasha/HW2_Lesta/3/3.txt
```

## 4. Настройте .gitignore, исключив один из подкаталогов от отслеживания.

```bash
echo "/1/" > .gitignore
```

```
➜  HW2_Lesta git:(master) ✗ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        2.bmp
        2/
        3/
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
```
➜  HW2_Lesta git:(master) ✗ git add .
➜  HW2_Lesta git:(master) ✗ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   .gitignore
        new file:   2.bmp
        new file:   2/2.txt
        new file:   3/3.txt
        new file:   README.md

➜  HW2_Lesta git:(master) ✗ git commit -m "Задания 1-4"
[master (root-commit) 9c39df1] Задания 1-4
 5 files changed, 68 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 2.bmp
 create mode 100644 2/2.txt
 create mode 100644 3/3.txt
 create mode 100644 README.md
 ```
## 5. Создайте две ветки от main: feature/api и feature/ui.

```bash
git branch feature/api
git branch feature/ui
```

➜  HW2_Lesta git:(master) ✗ git branch
```
  feature/api
  feature/ui
* master
(END)
```

## 6. В каждой ветке внесите независимые изменения. Сделайте как минимум по 2 коммита в каждой ветке с осмысленными сообщениями.

Ветка feature/api

```bash
git checkout feature/api
echo "Задание 6. Изменения в ветке feature/api" >> /home/sasha/HW2_Lesta/1/1.txt
git add .
git commit -m "Задание 6. Изменения в ветке feature/api"
echo "Задание 6. Изменения 2 в ветке feature/api" >> /home/sasha/HW2_Lesta/2/2.txt
<<<<<<< HEAD
git add .
git commit -m "Задание 6. Изменения 2 в ветке feature/api"
```
Веткаа feature/ui

```bash
git checkout feature/ui
echo "Задание 6. Изменения в ветке feature/ui" >> /home/sasha/HW2_Lesta/3/3.txt
git add .
git commit -m "Задание 6. Изменения 1 в ветке feature/ui"
echo "Задание 6. Изменения 2 в ветке feature/ui" >> /home/sasha/HW2_Lesta/3/3.txt
git add .
git commit -m "Задание 6. Изменения 2 в ветке feature/ui"
```

## 7. Выполните слияние ветки feature/api в main с использованием --no-ff.

```bash
git checkout master
git merge --no-ff feature/api -m "Слияние ветки feature/api в master"
git log --graph --oneline
```
➜  HW2_Lesta git:(master) git log --oneline --graph --all

```
*   ae5644e (HEAD -> master) Слияние ветки feature/api в master
|\  
| * 48487a5 (feature/api) Задание 6. Изменения 2 в ветке feature/api
| * c307581 Задание 6. Изменения в ветке feature/api
* | a57e332 Задание 6
* | b3bd339 Удалил ненужные картинки
|/  
| * ec0fedc (feature/ui) Задание 6. Изменения 2 в ветке feature/ui
| * 8969f8a Задание 6. Изменения 1 в ветке feature/ui
|/  
* 9c39df1 Задания 1-4
(END)
```

## 8. Выполните ребейз ветки feature/ui относительно main. Разрешите возможные конфликты. Зафиксируйте изменения.

```bash
git checkout feature/ui
git rebase master
```
➜  HW2_Lesta git:(feature/ui) git rebase master

```
Successfully rebased and updated refs/heads/feature/ui.
```

## 9. Создайте тег v1.0.0 на коммите, в котором объединены все изменения. Подпишите тег с сообщением.

```bash
git checkout master
git tag -a v1.0.0 -m "Релиз версии v1.0.0"
git tag # Проверяем, что создался
```

## 10. Иммитируйте ошибочный коммит в любой из веток. Отмените его с помощью git revert, а затем — другим способом с использованием git reset.

```bash
echo "ошибка" > zadanie10.txt
git add .
git commit -m  "Ошибочный коммит"
```
### Revert:

```bash
git revert HEAD
```

➜  HW2_Lesta git:(master) git revert HEAD
[master 5acdb99] Revert "Ошибочный коммит revert"
 1 file changed, 1 deletion(-)
 delete mode 100644 zadanie10.txt

➜  HW2_Lesta git:(master) git log --oneline

```
5acdb99 (HEAD -> master) Revert "Ошибочный коммит revert"
85c7694 Ошибочный коммит
3bdc7e1 (tag: v1.0.0) README
c81bffd README.md в .gitignore
ae5644e Слияние ветки feature/api в master
a57e332 Задание 6
b3bd339 Удалил ненужные картинки
48487a5 (feature/api) Задание 6. Изменения 2 в ветке feature/api
c307581 Задание 6. Изменения в ветке feature/api
9c39df1 Задания 1-4
(END)
```

### Reset

```bash
git reset --hard HEAD~1
git reset --hard HEAD~1
# Или сразу git reset --hard HEAD~2
```
➜  HW2_Lesta git:(master) git reset --hard HEAD~1

```
HEAD is now at 85c7694 Ошибочный коммит
```

➜  HW2_Lesta git:(master) git reset --hard HEAD~1

```
HEAD is now at 3bdc7e1 README
```

➜  HW2_Lesta git:(master) git log --oneline

```
3bdc7e1 (HEAD -> master, tag: v1.0.0) README
c81bffd README.md в .gitignore
ae5644e Слияние ветки feature/api в master
a57e332 Задание 6
b3bd339 Удалил ненужные картинки
48487a5 (feature/api) Задание 6. Изменения 2 в ветке feature/api
c307581 Задание 6. Изменения в ветке feature/api
9c39df1 Задания 1-4
~
~
~
~
(END)
```

## 11. Используйте git stash для сохранения незакоммиченных изменений. Затем восстановите их и продолжите работу.

```bash
echo "Задание 11" > zadanie11.txt
git status
```

➜  HW2_Lesta git:(master) ✗ git status

```
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        zadanie11.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
git add .
git stash save "Сохраняем изменения"
git status
```

➜  HW2_Lesta git:(master) git status

```
On branch master
nothing to commit, working tree clean
```

```bash
git stash list
```

➜  HW2_Lesta git:(master) git stash list

```
stash@{0}: On master: Сохраняем изменения
(END)
```

```bash
git stash apply stash@{0} # Оставляем копию в stash
git stash pop # Восстанавливает и удаляет из stash
```

➜  HW2_Lesta git:(master) git stash apply stash@{0}

```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   zadanie11.txt
```

# 12. Настройте удалённый репозиторий. Опубликуйте ветки, включая теги.

```bash
git remote add origin git@github.com:Mazurovsasha/lesta_hw2.git
git push -u origin master
git push origin v1.0.0
```