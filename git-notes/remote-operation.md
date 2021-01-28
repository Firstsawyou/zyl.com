# 远端操作

## 复制现有的远程数据库

```shell
$ git clone <url>
```

复制clone命令就会自动设定为追踪远程数据库 。这样，在执行push或fetch/pull命令时，即使省略repository，也可以正确地显示/读取修改内容。

## 复制现有的远程数据库

```shell
$ git remote add <name> <url>
```

## 显示远程数据库列表

```shell
$ git remote
```

添加-v选项就可以显示远程数据库的详细情况。

## 在远程数据库的分支创建本地数据库的分支

```shell
$ git checkout <branch>
```

使用最新版本的Git，用chekout命令参数指定远程数据库的分支，就可以通过远程数据库的分支在本地数据库创建分支。

## 在远程数据库创建分支／反映修改内容到分支

```shell
$ git push <repository> <refspec>
```

添加-u选项就可以追踪在远程数据库的目标分支。这样，在执行push或fetch/pull命令时即使省略了repository，也可以正确地显示/读取修改内容。

在repository，除了使用remote add命令添加的数据库名称外，也可以直接指定URL。如果省略repository，会指定被追踪的远程数据库。

在refspec可以指定分支名称。省略refspec的话，远程数据库和本地数据库所存有的分支会默认被列为目标。

## 查看远程数据库分支的修改内容

```shell
$ git fetch <repository> <refspec>
```

想确认远程数据库的修改内容，但不想反映内容到本地数据库时，可以使用fetch命令。使用fetch命令不会修改本地数据库的分支。

可以省略repository或refspec。而且省略repository与push的动作是相同的。如果省略refspec，所有的分支会默认被列为目标。

## 读取远程数据库的分支的修改内容

```shell
$ git pull <repository> <refspec>
```

通过pull命令，可以把远程数据库的修改内容反映到本地数据库的分支。贴士：「pull = fetch + merge」

可以省略repository或refspec。而且省略repository与push的动作是相同的。如果省略refspec，现在的分支会被列为目标。

## 删除远程数据库的分支

```shell
$ git push --delete <repository> <branchname>
```

在push命令指定--delete选项和<远程数据库名称> <要削除的标签> ，然后执行。

## 建立远程数据库的标签

```shell
$ git push <repository> <tagname>
```

添加-tags选项，就可以把本地数据库里所有的标签添加到远程数据库。

## 删除远程数据库的标签

```shell
$ git push --delete <repository> <tagname>
```

在push命令指定--delete选项和<远程数据库名称> <要削除的标签> ，然后执行。

## 修改已注册的远程数据库的电子邮件地址

```shell
$ git remote set-url <name> <newurl>
```

把已指定名称注册的远程数据库的电子邮件地址改为<newurl> 地址。

## 修改已注册的远程数据库

```shell
$ git remote rename <old> <new>
```

在<old>把已指定名称注册的远程数据库的名称改为<new> 。
