# Basic linux Commands
<details>
<summary> show/hide...
</summary>

### list files
`ls`

### show current working directory
`pwd`

### show your logged-in user-id
`whoami`

### change your directory

```cd /home```

`cd /Desktop`

### go back one directory
`cd ..`

### go back two directories
`cd ../../`

### go to the home page of the currently logged-in user
`cd ~`

### go directly to the root page
`cd /`

### copy file to a certain directory
`cp file ~/Desktop`

### change the file name or move it to another directory
`mv file1 file2`

`mv file1 ~/Documents`

### ping a target
`ping 10.1.1.1`

### traceroute
`traecroute 10.1.1.1`

### find a certain file
`ls | grep <filename>`


### create a file
`touch <filename>`
  
### edit a file
nano <filename>
  
### print somethingb into the screen
`echo hello`

`echo -e hi\nhow are you'

### create a file with contents
`echo -e hi\nhow are you' > greeting.txt`

### search for a word within a directory
`egrep -r hi`

### check the running services
`ps -aux`

</details>


# sort commands
sort command is used to sort files in descinding or assending order (Default Assending)

<details>
<summary> show/hide...
</summary>

## Preparing files for sorting
simply copy and past the below codes into your machine

`echo -e 'Firewall\nAntivirus\nIDS' > file.txt`

`echo -e '10\n100\n15\n20' > numfile.txt`

`echo -e 'server\nclient\nhost\nserver' > dupfile.txt`

`echo -e 'root    40%   1G\nlogs    53%   3M\nhome    20%   5G' > sheetfile.txt`


### Default Sort

```
sort file.txt
```

## Sort in Descending order

```
sort -r file.txt
```

## Sort in based on numeric values

```
sort -n numfile.txt
```

## Sort in based on numeric values in Descending order

```
sort -rn numfile.txt
```

## Sort the second column

```
sort -k 2n sheetfile.txt
```

## Sort and remove duplicates

```
sort -u dupfile.txt
```

## sorting through pip

```cat dupfile.txt | sort```

</details>


