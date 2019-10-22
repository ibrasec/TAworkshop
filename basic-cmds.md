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
`nano <filename>`
  
### print somethingb into the screen
`echo hello`

```
echo -e hi\nhow are you
```

### create a file with contents
`echo -e 'hi\nhow are you' > greeting.txt`

### search for a word within a directory
`egrep -r hi`

### check the running services
`ps -aux`

### read from a file
`cat <filename>`


### Count how many lines in the file
```
cat file.txt | wc -l
```



</details>



# Bash Scripting
Commands to use when in need

<details>
<summary> show/hide...
</summary>
``` for i in {1..5}; do echo $i;sleep 0.5;done```

</details>

# airmon

<details>
<summary> show/hide...
</summary>
  
### enable the Wireless interface to be in moitoring mode
issue the `ifconfig` command to find the wireless interface id, in my case it is `wlp2s0`
sudo airmon-ng start wlp2s0  

once you do this command you should find a newly created interface when you do the `ifconfig` command as example mon0,mon1...etc

### Start finding Nearby Access points

sudo airodump-ng start mon0
  
  
### Start finding Nearby Access points
The below command will search the nearby AP names with thier MAC Address and the working channel id

sudo airodump-ng -w ~/foundAp mon0

### After finding out the access point name

sudo airodump-ng --essid 'ACCESSPOINT-NAME' --bssid 'AA:BB:CC:DD:EE:FF' -w ~/CapturedAP mon0 -c <channel id>
  
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



# tshark
tshark is the command line tool for wireshark to read pcap files

<details>
<summary> show/hide...
</summary>
  
### To show the installed version of Tshark
```
tshark -v
```
### To Find all Tshark supported network interfaces for monitoring
```
tshark -D
```
### sniff traffic on eth0

***Note: this needs permission***

```
tshark -i eth0
```

### Read a pcap file and display it into the console
```
tshark -r traffic.pcap
```
### To find the totoal number of packets in a certain pcap file?
```
tshark -r traffic.pcap | wc -l
```
### Read the first 10 packets? 
```
tshark -r traffic.pcap -c 10
```
### Print the list of protocols in HTTP_traffic.pcap  
```
tshark -r traffic.pcap -z io,phs -q
```

### command to show only the HTTP traffic from a PCAP file
```
tshark -Y 'http' -r traffic.pcap
```

### command to export data transferred through HTTP
```
tshark -nr record-http.pcap --export-objects http,tsharkfile
```


### command to show the IP packets sent from IP address 192.168.1.1 to IP address 1.1.1.1

```
tshark -r traffic.pcap -Y "ip.src==192.168.1.1 && ip.dst==1.1.1.1"
```

### command to print packets containing GET requests

```
tshark -r traffic.pcap -Y "http.request.method==GET"
```

### command to used to print only source IP and URL for all GET request packets

```
tshark -r traffic.pcap -Y "http.request.method==GET" -Tfields -e frame.time -e ip.src -e http.request.full_uri
```

### To know How many HTTP packets contains the "password" string or any other string

```
tshark -r traffic.pcap -Y "http contains password”
```
### To know the destination IP address for GET requests sent for yahoo.com

```
tshark -r traffic.pcap -Y "http.request.method==GET && http.host==www.nytimes.com" -Tfields -e ip.dst
```

</details>


# Referneces
- http://www.unit-conversion.info/texttools/
- wireshark
- tshark
- virustotal
- capanalysis
  
