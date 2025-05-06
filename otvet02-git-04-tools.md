# Домашнее задание к занятию «2.4. Инструменты Git» - Храмов Александр






# Задание

# 1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.

*Команда:*
```bash
root@git:/home/alex/web/gittest/terraform# git show aefea --pretty=format:'Hash = %H %nComment: %s' -q
```
*Результат:*
```bash
Hash = aefead2207ef7e2aa5dc81a34aedf0cad4c32545 
Comment: Update CHANGELOG.md
```
# Ответьте на вопросы.

### Какому тегу соответствует коммит 85024d3?

*Команда:*
```bash
root@git:/home/alex/web/gittest/terraform# git show 85024d3 --oneline -q
```
*Результат:*
```bash
85024d310 (tag: v0.12.23) v0.12.23
```
Ответ: *tag: v0.12.23*

### Сколько родителей у коммита b8d720? Напишите их хеши.

*Команда:*
```bash
root@git:/home/alex/web/gittest/terraform# git show --source b8d720 --pretty=short 
```
*Результат:*
```bash
commit b8d720f8340221f2146e4e4870bf2ee0bc48f2d5 b8d720
Merge: 56cd7859e 9ea88f22f
Author: Chris Griggs <cgriggs@hashicorp.com>

    Merge pull request #23916 from hashicorp/cgriggs01-stable
```
Ответ: *Merge: 56cd7859e 9ea88f22f* 2 родителя.

### Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24.

```bash
root@git:/home/alex/web/gittest/terraform# git log v0.12.23..v0.12.24^ --pretty=oneline 
```
Ответ:
```bash
b14b74c4939dcab573326f4e3ee2a62e23e12f89 [Website] vmc provider links
3f235065b9347a758efadc92295b540ee0a5e26e Update CHANGELOG.md
6ae64e247b332925b872447e9ce869657281c2bf registry: Fix panic when server is unreachable
5c619ca1baf2e21a155fcdb4c264cc9e24a2a353 website: Remove links to the getting started guide\'s old location
06275647e2b53d97d4f0a19a0fec11f6d69820b5 Update CHANGELOG.md
d5f9411f5108260320064349b757f55c09bc4b80 command: Fix bug when using terraform login on Windows
4b6d06cc5dcb78af637bbb19c198faff37a066ed Update CHANGELOG.md
dd01a35078f040ca984cdd349f18d0b67e486c35 Update CHANGELOG.md
225466bc3e5f35baa5d07197bbc079345b77525e Cleanup after v0.12.23 release
```



### Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...) (вместо троеточего перечислены аргументы).

*Команда:* 
```bash
root@git:/home/alex/web/gittest/terraform# git log -S'func providerSource(' --pretty=oneline 
```

Ответ: 
```bash
8c928e83589d90a031f811fae52a81be7153e82f main: Consult local directories as potential mirrors of providers
```

### Найдите все коммиты в которых была изменена функция globalPluginDirs.
*Команда: *
```bash
root@git:/home/alex/web/gittest/terraform/terraform# git grep -oi --heading --break -e 'func globalPluginDirs'
```
*Результат:*
```bash
plugins.go
func globalPluginDirs
```
*Команда:* 
```bash
root@git:/home/alex/web/gittest/terraform/terraform# git log -L:'GlobalPluginDirs':internal/command/cliconfig/plugins.go --oneline -q
```
Ответ:
```bash
7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
78b1220558 Remove config.go and update things using its aliases
52dbf94834 keep .terraform.d/plugins for discovery
41ab0aef7a Add missing OS_ARCH dir to global plugin paths
66ebff90cd move some more plugin search path logic to command
8364383c35 Push plugin discovery down into command package
```
###  Кто автор функции synchronizedWriters?
*Команда:* 
```bash
root@git:/home/alex/web/gittest/terraform/terraform# git log -S'func synchronizedWriters' --first-parent --pretty=format:'%an "%ae"'
```
Ответ:
```bash
James Bardin "j.bardin@gmail.com"
Martin Atkins "mart@degeneration.co.uk"

```

