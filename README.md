# forall

## Installation

Download and make it executable:
```
wget https://raw.githubusercontent.com/WhiteBlackGoose/forall.bash/main/forall
chmod +x forall
```

Add it to your "$PATH":
```
echo 'export PATH="yourfolder:$PATH"' >> ~/.bashrc
```

## Docs

```
Automates simple loops. Basically maps the given 
elements through the given function.

The first argument is list of elements (must be o
ne argument, not multiple).

The second argument is the command to execute (al
so must be one string).

By default it only executes the given command, by
providing each element of the list as the last ar
gument.

Arguments (provide as third argument without dash):

    i: provide each element as standard input inste
       ad of providing it as the last argument.

    p: print the each element next to correspondi
       ng output. (by default only runs the prompt)
```

## Examples

### Ex. 1

```
forall "$(ls -Cb)" "du -sh"
```

Runs the command `du -sh` for all folders in the given folder:
```
~/VirtualBox VMs
12:06:29 $ forall "$(ls -Cb)" "du -sh"
6,7G	archcraft
11G	Linux Mint
8,0K	test
88K	ubuntu 4.10
9,2G	ubuntu mate
```

### Ex. 2

```
forall "10+3 12-11 'scale=3; 100/3'" bc i
```

`i` means that we pipe each element into the given command `bc`. Output:

```
~/VirtualBox VMs
12:38:02 $ forall "10+3 12-11 'scale=3; 100/3'" bc i
13
1
33.333
```

### Ex. 3

Let's add `p` to print each input:
```
forall "10+3 12-11 'scale=3; 100/3'" bc ip
```

Output:
```
~/VirtualBox VMs
12:38:50 $ forall "10+3 12-11 'scale=3; 100/3'" bc ip
10+3: 13
12-11: 1
scale=3; 100/3: 33.333
```
