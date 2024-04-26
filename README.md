# Wireshark
This lab highlights a couple of the uses of Wireshark. I began by capturing and analyzing network traffic using a Kali Linux VM. I then used Wireshark to enumerate hosts and ports to determine OS type and other system information. 

Wireshark is a network protocol analyzer. It allows you to inspect and capture packets on your network. It allows you to inspect the traffic that is transmitting on your network. Wireshark provides a user interface that allows you to filter your network traffic and analyze that traffic. A system administrator can use Wireshark if they suspect there might be nefarious traffic that the firewall and/or intrusion detection system is not catching. A system administrator needs to know the protocols in depth to grasp the information being transmitted on the network. 

<h2>Step 1 - Log on to your Kali Linux VM and Open a Terminal</h2>

Use the **ifconfig** command to determine the IP address of the VM. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/6c6efee3-aeb5-4145-92a9-b550f930ae53)

<h2>Step 2 - Hide the IP Address of the VM</h2>

Next, use the **if config eth0 0.0.0.0 up** command so that our VM does not have an IP address. This has many uses including: Security/Privacy, Avoiding Geo-Blocking, Preventing Tracking, Avoiding IP-based Bans, and Enhancing Anonymity. We are doing this in this lab for privacy concerns and network segmentation. It will allow us to  capture traffic from an intended segment without revealing unnecessary information about other segments. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/96c780c3-44b5-43ea-be3a-9f5e5f494e1c)

Verify that no IP address is listed by using the command **ifconfig** again. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/7c82cd26-1c32-45cd-bdbc-b3d77775579a)

<h2>Step 3 - Launch Wireshark</h2>

In the terminal, use the command **Wireshark**. I already had wireshark installed on my VM, but if you need to install it onto yours, you can visit: (https://www.wireshark.org/download.html). 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/42384330-6fce-4680-a7eb-295cb5f081f5)

When the **Lua: Error during loading** pop-up shows, click **OK**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/df9ea21e-38c3-431b-b211-e6944254675c)

Once the Wireshark GUI opens, click on **Capture** in the banner and choose **Interfaces**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/d2e62f29-28da-4f59-855e-f2b33c351e33)

Select the check box next to **eth0**. The IP column should say "none". Click **Start**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/cd4b0f4f-84cb-4daa-8e1d-60ebbd374d10)

Both panes should begin to populate with packets. Allow some time to pass before moving on. After a couple minutes, minimize the Kali Linux VM or move it to another monitor. 

<h2>Step 4 - Open a Windows VM</h2>

Start up your Windows 10 VM and once opened, begin a command line and select to **run as administrator**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/bc2053b8-6ca3-4de1-900d-7f11dbe8eb01)

In the command line, we need to go to the C drive. Use the command, **cd \**

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/be313d4e-a20b-4267-b0c1-25765ea68e7c)

Now we need to move to the Windows Server using FTP. Use the command **ftp** to connect to the Windows Server. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/bdea97ae-43f4-48fa-b70e-c667ad885033)

For the **User** and **password**, identify one of the user profiles on your VM/Server and connect to it using the correct password combination. Once connected to the VM Server, use the **ls** command to list all the files and folders. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/59ad1604-b5df-498e-a6b0-4717f812148c)

Try accessing different files from the command line on the Windows 10 VM. In my particular lab, I then switched to binary mode, using **bin**, and accessed a jpg file on the server machine.  

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/3b1f63a1-7267-40a3-a86c-f4c00b288230)

Exit **ftp** by using the **bye** command and then close the cmd by using the **exit** command. 

<h2>Step 5 - Open The Extracted Server File</h2>

On the Windows 10 VM, go to **File Explorer**. Then click, **This PC**, and then double-click on **Local Disk (C:)**

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/300c2cd5-883b-48bf-be22-4f1c175be921)

You shoud now be able to see the extracted server file. 

<h2>Step 6 - Connect to the Windows Server Using Telnet</h2>

Open the cmd-shortcut and use the **telnet** command and server IP to connect to your server. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/d63158db-35bd-4781-b465-4f10ffabb4ab)

Type **y** when asked about sending your password information to a remote computer and press enter. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/79ed1d4b-eb23-48d5-aa81-4c51e79ba638)

Log in to your Windows Server as an admin using the admin account you've set up for the server. 

<h2>Step 7 - Add "Creeper" Account Through Telnet</h2>

On the same command line, add the user "creeper" by typing **net user creeper P@ssw0rd /add**.

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/32af25da-59fd-4b96-b30e-4298bab47f65)

Now, add "creeper" to the Enterprise Admins group using **net group "domain admins" creeper /add**

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/69b1741e-dbcb-4809-92c0-8132fa039fd7)

Exit the telnet session by using the **exit** command. 

<h2>Step 8 - Create Email Traffic to Analyze on Windows VM</h2>

On the Windows 10 VM, open an email account (in this particular lab, my VM had 'Opera Mail' installed). Compose a message and send to one of your email accounts. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/0e3cc08f-df06-4d3d-943b-10fa777bd713)

<h2>Step 9 - Analyzing the Traffic</h2>

Go back to you Kali Linux VM and in the Wireshark Filter pane, **frame contains zombie** (zombie is the password of the admin account for my VM). FTP is in plain text, so we should be able to filter out the password of the VMs that we sent over FTP. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/6622bc3d-49ca-40fa-a872-8e1780110905)

Next, we will examine the email traffic we created. POP is also in plain text, so we should be able to see the user password. In the Wireshark Filter pane type, **pop**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/7bb8ac29-957a-40db-af40-5a06486503a6)

Now filter Wireshark to show apart of your email message. In my email, we sent the message "You should buy minecraft", so I filtered Wireshark using **frame contains buy**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/563d5f46-4013-4966-8107-4897b86ace5b)

On that filter screen, right-click on the POP frame and select **Follow TCP Stream**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/9e75325f-642c-42d8-a575-b6a1bad6744d)

You can now scroll down through the TCP stream and read the email you sent. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/7647f02a-86be-408d-af32-37c7450900cb)

Close the TCP Stream. Back in the Wireshark Filter pane, filter the packets by **telnet**. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/07c75bdd-f26a-43b4-9384-c888ca85cbc1)

Right-click on the first telnet frame and follow it's TCP stream. At the bottom of the window, click on **Entire Converstaion** and select the bottom choice. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/c0f2d528-86c6-419f-a4e7-838e7c62f5b8)

You should be able to see the command where we created the user "creeper", the password we chose, and the group we assigned it to. 

![image](https://github.com/amolinaro23/Wireshark/assets/164687651/959a82f0-3006-451f-9f41-8acaa7419e71)

<h2>Step 10 - </h2>
