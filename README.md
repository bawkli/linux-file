**Mothod 1: Using SCP(Secure Copy)**

SCP is a simple and secure way to trnsfer files over SSH between two computers.

1: Prerequisites:
   - Both PC1 and PC2 myst have SSH installed
   - PC1 needs to know PC2's IP address(e.g., 192.168.1.101).
   - PC2 much have an SSH server running:
     bash
      sudo apt update
      sudo apt install openssh-server
      sudo systemct1 enable ssh
      sudo systemct1 start ssh

2. On PC1(Sender):
   - Find the file you want to share(e.g., /home/user1/file.txt).
   - Use SCP to send it to PC2:
     bash

      ``` scp /home/user1/file.txt user2@192.168.1.101:/home/user2/ ```

     - Replace user2 with the username on PC2
     - Replace 192.168.1.101 with PC2's IP address (find it on PC2 with ip addr show).
     - Replace /home/user2/ with the destination path on PC2.

On PC2 (Receiver):
  - Enter the password for user2 when prompted (unless SSH keys are set up).
  - Check the file in /home/user2/.

**Method 2: Using SFTP (Secure File Transfer Protocol)**

SFTP provides an interactive way to transfer files over SSH.

1. On PC2:
    - Ensure the SSH server is running (see Method 1).
2. On PC1:
   - Start an SFTP session:
     bash
     
     ```sftp user2@192.168.1.101```
     
   - Enter the password for user2.
  
3. In the SFTP Prompt:
   - Upload the file:
     bash
     put /home/user1/file/txt
   - The file goes to the default home directory on PC2 (/home/user2/ ), or specify a path:
  
     bash
     put /home/user1/file.txt /home/user2/shared/
   - Exit SFTP
      bash
      exit

