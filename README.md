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


