**For ansys Electronics Desktop see the other section "Using ansysHFFS on the cluster" in the guide**

### Prerequisites
Ansys RSM must be installed on your personal computer.
You need to be connected to the RTU network - either directly or indirectly through a VPN.
You also need to add the key as decribed in the next section and then go throug the "Setting up RSM" section.
  
### Adding keys for ansys on the cluster

Step 1: Download and install PuTTY.
Download and install PuTTY from the following location:
http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
If this link is invalid, perform a web search for "PuTTY".

Step 2: Create a cryptographic key.
Create a cryptographic key using PuTTYGen (puttygen.exe) as follows:
1. On the PuTTY Key Generator dialog box, click Generate.
2. Change the Key comment to include your machine name and Windows username.
3. Do not enter a key passphrase.
4. Save the private key file without a passphrase.
For example, <drive>:\Program Files\Putty\id_rsa.ppk.
If you use a passphrase, jobs will hang a prompt for you to enter the passphrase. Be sure to secure the private key
file using some other means. For example, if only you will be using the key, save it to a location where only you
and administrators have access to the file, such as the My Documents folder. If multiple users share the same key,
allow the owner full control, then create a group and give only users in that group access to this file.
5. If your Linux cluster uses OpenSSH, convert the key to OpenSSH format by selecting Conversions > Export Open
SSH key in the PuTTY Key Generator dialog box.

6. Move the public portion of the key to the Linux machine. This requires you to edit the
~/.ssh/authorized_keys file on the Linux machine as follows:
a. Type: nano ~/.ssh/authorized_keys 
b. Copy all the text from the box under Public key for pasting and paste it into ~/.ssh/authorized_keys.
All of this text should be one line. If some keys exist, add a new line.
c. Ctrl + x and then press y

Step 3: Modify system environment variables.
1. Open the Windows System Properties dialog box.
2. On the Advanced tab, select Environment Variables. The Environment Variables dialog box appears.
3. In the Environment Variables dialog box, locate the Path variable in the System variables pane.

4. Select the Path variable and then click the Edit button. The Edit System Variable dialog box appears.
5. Add the PuTTY install directory to the Variable value field (for example, C:\Program Files\putty) and
then click OK.

6. In the System variables pane, click the New button. The New System Variable dialog box appears.
7. In the New System Variable dialog, create a new environment variable named KEYPATH with a value containing
the full path to the private key file (for example, <drive>:\Program Files\Putty\id_rsa.ppk).

Use a user variable if the key file is used only by you. Use a system variable if other users are sharing the key file.
For example, if a Windows 7 user has a key file in My Documents, the variable value should be
%USERPROFILE%\My Documents\id_rsa.ppk (this expands to <drive>:\Documents and
Settings\<user>\My Documents\id_rsa.ppk).
8. Click OK.
9. Reboot the computer for environment changes to take effect.

Step 4: Perform an initial test of the configuration.
1. Run the following from the command prompt (quotes around %KEYPATH% are required):
plink -i "%KEYPATH%" unixlogin@unixmachinename pwd
2. When prompted by plink:
If plink prompts you to store the key in cache, select Yes.
If plink prompts you to trust the key, select Yes.

### Setting up RSM
Open ansysRSM on your machine. 

You should see the following screen. Press the button to add a new cluster(marked with a red arrow).
![ansys_simulate_select](images/ansysRSM/initial.png)

Now enter a name for the new cluster on the right side under the HPC configuration header. For the HPC type choose "**custom**". In the submit host enter "**ui-2.hpc.rtu.lv**". In the custom HPC type enter "**TORQUE**". Check the "**Use HPC protocol...**" checkbox and select "**Able to directly submit and monitor HPC jobs**". Lastly click **Apply** at the bottom.
![ansys_simulate_select](images/ansysRSM/settings1.png)

In the second settings screen set everything as shown in the following image, but change the part "**yourUserAccount**" to your actual HPC account username. Click **Apply**.
![ansys_simulate_select](images/ansysRSM/settings2.png)

First double click on the credentials tab on the left side then click the button on the right panel to create new credentials. 
![ansys_simulate_select](images/ansysRSM/creds1.png)

In the promt that appears enter your HPC username and the password that you use to login to the HPC cluster
![ansys_simulate_select](images/ansysRSM/creds2.png)

Select the cluster that you just created and any others where you wish to use this account.
![ansys_simulate_select](images/ansysRSM/creds3.png)

Go back to the cluster setup by double clicking on the cluster name

![ansys_simulate_select](images/ansysRSM/goback.png)

Select the queues tab(1.). Then press the button(2.) to load the queues from the cluster. Check the queues that you will need to use in the **Enabled** column. Finally, test if the queues work by clicking the submit button(3.) and if everything is setup correctly you should see a green checkmark next to the submit button. Click **Apply**.

![ansys_simulate_select](images/ansysRSM/settings3.png)
