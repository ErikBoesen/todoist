Todoist CLI client
===

[Todoist](https://todoist.com/) CLI Client, written in Golang.

## Description

[Todoist](https://todoist.com/) is a cool TODO list web application.
This program will let you use the Todoist in CLI.

![color image](https://cloud.githubusercontent.com/assets/6121271/20603278/2261b424-b2a4-11e6-8fa7-d533e2144942.png)

## Demo (with [peco](https://github.com/peco/peco))

### Add Task

![Add task](https://cloud.githubusercontent.com/assets/6121271/19836528/6ed99956-9ee6-11e6-85b0-7539393d803b.gif)

### Close Task

![Close task](https://cloud.githubusercontent.com/assets/6121271/19836531/7c399218-9ee6-11e6-974c-9dd59ced13a5.gif)

## Usage

```
$ todoist --help
NAME:
   todoist - Todoist CLI Client

USAGE:
   todoist [global options] command [command options] [arguments...]

VERSION:
   0.10.1

COMMANDS:
     list, l                  Show all tasks
     show                     Show task detail
     completed-list, c-l, cl  Show all completed tasks (only premium users)
     add, a                   Add task
     modify, m                Modify task
     close, c                 Close task
     delete, d                Delete task
     labels                   Show all labels
     projects                 Show all projects
     karma                    Show karma
     sync, s                  Sync cache
     quick, q                 Quick add a task
     help, h                  Show a list of commands or help for one command

GLOBAL OPTIONS:
   --color              colorize output
   --csv                output in CSV format
   --debug              output logs
   --namespace          display parent task like namespace
   --indent             display children task with indent
   --project-namespace  display parent project like namespace
   --help, -h           show help
   --version, -v        print the version
```

### `list --filter`

You can filter tasks by `--filter` option on `list` subcommand.
The filter syntax is base on [todoist official filter syntax](https://support.todoist.com/hc/en-us/articles/205248842-Filters).

Supported filter is [here](https://github.com/sachaos/todoist/issues/15#issuecomment-334140101).

#### e.g. List tasks which over due date and have high priority

```
todoist list --filter '(overdue | today) & !p1'
```

## Config

Config stored in `$HOME/.todoist.config.json`

It has following parameters:

```
{
  "token": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx", # todoist api token, required
  "color": "true"                                      # colorize all output, not required, default false
}

```

## Install

### Homebrew (Mac OS)

```
$ brew tap sachaos/todoist
$ brew install todoist
```

### Build it yourself

You need version 1.7 or higher Golang, and [golang/dep: Go dependency management tool](https://github.com/golang/dep).

```
$ mkdir -p $GOPATH/src/github.com/sachaos
$ cd $GOPATH/src/github.com/sachaos
$ git clone https://github.com/sachaos/todoist.git
$ cd todoist
$ make install
```

### Register API token

When you run `todoist` first time, you will be asked your Todoist API token.
Please input Todoist API token and register it.

### Sync

After register API token, you should sync with todoist.com by `sync` sub command, like below.

```
$ todoist sync
```

### Use with peco

**RECOMMENDED**

install *peco* and load `todoist_functions.sh` on your `.zshrc`, like below.

fish version is here. [ka2n/fish-peco_todoist](https://github.com/ka2n/fish-peco_todoist) Thanks @ka2n!

```
$ source "$GOPATH/src/github.com/sachaos/todoist/todoist_functions.sh"
```

#### keybind

```
<C-x> t t: select task with peco
<C-x> t p: select project with peco
<C-x> t l: select labels with peco
<C-x> t c: select task and close with peco
<C-x> t d: select date
<C-x> t o: select task, and open it with browser when has url
```

## TODO

* Refactoring
* Restrict view option

## Author

[sachaos](https://github.com/sachaos)
