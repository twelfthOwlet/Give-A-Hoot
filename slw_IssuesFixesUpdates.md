#### Updates, Issues, and Fixes - A diary of experiences, fixes, methods, etc.


<pre>
 Maintenance stuff:  https://github.com/twelfthOwlet/Give-A-Hoot/blob/main/slw_Automobile_README.md 
                     https://github.com/twelfthOwlet/Give-A-Hoot/blob/main/slw_Bicycle_Rebuild_README.md    
</pre>

December 2023

###### Ubuntu Monitor Yellow Tint 
<pre> 
 -> Most Recent: OS Ubuntu 22.04.3: Yellow tint after installing 2nd monitor.  
  --> Found incorrect video driver auto-installed.  Installed correct Nvidia driver package 
       to correct yellow coloration.  Version not stated to prevent compatibility issues.
</pre>  
###### Ubuntu Studio VM Upgrade
<pre>
-> Updating Ubuntu Studio VM from 20.04 to 22.04 from command line.  
  --> First time experiencing the do-release-upgrade command.  
      **Thanks to: https://ubuntu.com/server/docs/upgrade-introduction 

  --> Choice between sddm and lightdm.  lightdm chosen.
  --> Upgrade to firefox snap?  hmm.  No choice?  ok. 
  --> Completed upgrade: ~2 hours
</pre>

###### Redhat/CentOS7 VM and SSH Issue (Reminder: CentOS 7 EOL June 30,2024)
<pre>
 Dec 26, 2023: Installed Redhat Enterprise 9 w/no issues into VirtualBox. SSH and IP assignment issue.
   -- No network communication between RH Guest and Host but can access web. 
   -- VM Manager has own DHCP server.  Default IP assigned and NAT-ted.
   -- Changed IP address, net mask, etc.  Could ping host/web, but no ping from host.
   -- Forgot to bridge the network adapter rather than use NAT.
   -- ssh'd in, no issue.

 Dec 27, 2023: Decided to use CentOS 7 instead. Deleted RH9 from VM. SSH issue again, as suspected.
   -- Since this was a minimum install, configured everything for Guest network via config files through vi.
   -- Applied lessons learned from day before- bridged the adapter.  
   -- Installed net-tools to check if port 22 is open and for routing information
   -- Open.  Attempt to log into ssh and Host complains of a different remote host attached to IP address.
   -- Doh.  Yeah, the RH install, lol. Had to:
      -> ssh-keygen -f "/home/user/.ssh/known_hosts" -R "xxx.xx.x.xx"
   -- Logged into Guest through ssh.
</pre>
<pre>
   -- Found SMTP port open??? Perhaps for rsyslog?
   -- Installed nc(nmap version) and attempted connection to make sure it is live-- yep.
   -- Checked services(systemctl) for a relation to smtp, nothing seen or grepped.
   -- Out of time today but this is giving me some re-education of Linux commands on RH-based OS. 
</pre>
