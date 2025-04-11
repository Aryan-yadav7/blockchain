# IPFS-
The InterPlanetary File System (IPFS) is a decentralized, peer-to-peer protocol for storing and sharing files, aiming to create a more resilient and efficient internet by distributing data across a network of computers. 

Installation of IPFS on local machine. Further, upload the files (such as photos, audio, and video) on IPFS and share it with other through content identifier (i.e., hash). Perform assessment using ubuntu WSL.
Commands (IPFS)
1.	Install the IPFS through WSL: wget https://dist.ipfs.tech/kubo/v0.32.1/kubo_v0.32.1_linux-amd64.tar.gz 
Or 
wget https://github.com/ipfs/kubo/releases/download/v0.32.1/kubo_v0.32.1_linux-amd64.tar.gz
2.	tar -xvzf kubo_v0.32.1_linux-amd64.tar.gz
3.	Kubo is a reference implementation of IPFS in Go: cd kubo 
4.	ls
5.	sudo bash install.sh
6.	ipfs –version
7.	ipfs init
8.	ipfs daemon
9.	On Browser: http://127.0.0.1:5001/webui
10.	To run ipfs daemon in background: ipfs daemon > ipfs.log 2>&1 &
11.	This is daemon ID: [1] 772
12.	Add file: echo "Hello, IPFS!" > hello.txt
13.	ipfs add hello.txt
14.	ipfs cat <CID>
15.	Add a directory: 
mkdir myfolder
echo "File 1 content" > myfolder/file1.txt
echo "File 2 content" > myfolder/file2.txt
16.	ipfs add -r myfolder
17.	ps aux | grep ipfs
18.	kill <PID>
19.	in Browser you can directly run this to see the IPFS: https://ipfs.io/ipfs/QmWd9cavD8UGZQcqYBVhZqs2Jure5W9cgxR7S6TC4StfZe

![Screenshot (22)](https://github.com/user-attachments/assets/828f495b-1e1b-4481-824a-93fdc47592a0)

![Screenshot (20)](https://github.com/user-attachments/assets/41c86622-518e-4448-b91c-e5ee42e719bd)

![Screenshot (21)](https://github.com/user-attachments/assets/638d9537-df7a-47ea-bec7-efe965e235f9)

