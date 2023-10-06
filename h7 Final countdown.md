# Table of contents

- Links to my reports
- Presentation cross evaluation
- Install a firewall on Linux and block all ports that are not needed
- Ssherver: Install OpenSSH server and connect to it

# Links to my reports

> h0: https://github.com/piafernandez/Information-Security-2023/blob/main/h0-hello-world.md

1. h1 First steps: https://github.com/piafernandez/h1-First-Steps/blob/main/h1-First-Steps.md
2. h2 Spiderwebs: https://github.com/piafernandez/h2-Spiderwebs/blob/main/h2%20Spiderwebs.md
3. h3 Should Tero wear a helmet?: https://github.com/piafernandez/h3-Should-Tero-wear-a-helmet-/blob/main/h3%20Should%20Tero%20wear%20a%20helmet%3F.md
4. h4 ETAOIN: https://github.com/piafernandez/h4-ETAOIN/blob/main/h4%20ETAOIN.md
5. h5 September2023!: https://github.com/piafernandez/h5-September2023/blob/main/h5%20September2023!.md
6. h6. A. Nynomous: https://github.com/piafernandez/h6-A.-Nynomous/blob/main/h6%20A.%20Nynomous.md
7. h7. Final countdown: https://github.com/piafernandez/h7-Final-countdown/blob/main/h7%20Final%20countdown.md

# Presentation cross evaluation

> Please see in Moodle :) I will update for presentations day 2.

# Install a firewall on Linux and block all ports that are not needed

1. Open your virtual machine

2. Open your terminal

3. Ensure your Linux system is up to date:

   ```
   sudo apt-get update
   ```

   <img width="415" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/e660f917-a161-4663-b3bd-9e4ed4ca55a0">


4. Check UFW Status (if already installed)

   > If UFW is not installed, it will show as inactive. If it's installed, it will display its current status (active or inactive).

   ```
   sudo ufw status
   ```

   <img width="233" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/31b89d4f-c845-4a9c-abb5-48d289ec0904">

5. Install the Uncomplicated Firewall (UFW):

   > If UFW is not installed, you can install it using the following command:

   ```
   sudo apt-get install ufw
   ```

   Mine was already installed:

   <img width="399" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/9d8a55c1-0630-47fd-a9bf-9f786e773ef7">


6. Allow incoming SSH connections:

   > To block all ports that are not needed, you'll want to allow only the necessary ports and deny all others. For example, if you want to allow SSH (port 22) and HTTP (port 80) while blocking all other ports:

   ```
   sudo ufw allow 22/tcp  # Allow SSH
   sudo ufw allow 80/tcp  # Allow HTTP
   sudo ufw allow 443/tcp # Allow HTTPS
   ```

   <img width="281" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/acb3ac74-4d72-4dda-98fb-ad2fd39fda72">


7. Enable the firewall to start protecting your system:

   > This will activate the firewall with the defined rules, and it will start blocking all incoming connections except for the allowed ports.

   ```
   sudo ufw enable
   ```

   <img width="307" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/4a4fcd43-3eca-4aab-92e7-f62697c7296b">


8. Check UFW Status: 

   > Verify that UFW is active with your configured rules:

   ```
   sudo ufw status
   ```

<img width="347" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/f80bdf0c-36f4-4a3b-be3a-db4ad9918646">


Your Linux system now has a firewall (UFW) in place, and it's blocking all ports that you haven't explicitly allowed. 

# Ssherver: Install OpenSSH server and connect to it

1. Open your virtual machine

2. Open your terminal

3. Ensure your Linux system is up to date:

   ```
   sudo apt-get update
   ```

4. Install the OpenSSH server:

   ```
   sudo apt-get install openssh-server
   ```

   <img width="409" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/7ef3787e-cba6-414c-9f5e-235c98311381">


5. Start the SSH server:

   ```
   sudo systemctl start ssh
   ```

6. Create a New User (Optional):

   > If you want to enhance security by creating a dedicated user for SSH access:

   ```
   sudo adduser alice
   ```

   <img width="377" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/fb4c8007-1e9f-485c-8355-6a749820e66c">


   > Be sure to set a strong password for the new user.

6. Switch to user Alice

   ```
   su alice
   ```

   <img width="221" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/8c0b9f84-5144-4215-a447-60ba9a8cb317">


7. Check which user you are

   ```
   whoami
   ```

   <img width="242" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/e9551de5-8a9d-4e01-af07-e94b0f373c4d">


8. Generate SSH keys

   ```
   ssh-keygen
   ```

   <img width="410" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/a1f3fa26-5f74-427b-a0da-fceeb7305af7">


9.  Copy the public SSH key of Alice

   > The command `ssh-copy-id alice@127.0.0.1` is used to copy the public SSH key of the user "alice" from your local machine to the same machine you are currently on (localhost) using SSH key-based authentication.

   ```
   ssh-copy-id alice@127.0.0.1
   ```

   <img width="413" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/3e7f0649-d93b-43c4-bee5-bc62f4604c20">


10. Test SSH Key Authentication for Alice

    > After copying Alice's SSH key, you can now test SSH key authentication to ensure it's working correctly. Run the following command to connect to the remote server as Alice:

    ```
    ssh alice@127.0.0.1
    ```

    > If everything is set up correctly, you should be able to log in without entering a password. You'll be using Alice's private key stored on your local machine for authentication.

    <img width="412" alt="image" src="https://github.com/piafernandez/h7-Final-countdown/assets/71267247/bca095f2-bb55-4b64-9933-eadbc625c783">


# Sources and Links 

- *Instant Firewall – Sudo Ufw Enable | Tero Karvinen*. https://terokarvinen.com/2016/09/08/instant-firewall-sudo-ufw-enable/?fromSearch=firewall. Accessed 6 Oct. 2023.
- *ChatGPT - OpenAI* [ChatGPT (openai.com)](https://chat.openai.com/?model=text-davinci-002-render-sha) Accessed 6 October. 2023.


