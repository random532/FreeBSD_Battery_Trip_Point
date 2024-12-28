# FreeBSD Battery Warnings

Affected file:<br>
sys/dev/acpica/acpi_cmbat.c<br>

<br>

__Short description:__<br>
You don't need to poll the battery periodically.<br>
You can set a percentage (ranging from 0-100) via sysctl.<br>
This causes a /dev/devd event Notify(0x80). So a script can be triggered.<br>
<br>

__Long description:__<br>
ACPI specification defines an optional acpi method called "_BTP". <br>
Currently the FreeBSD cmbat driver only supports mandatory methods (bif, bix, ..), but no optional ones.<br>

Try the command: "acpidump -dt |grep _BTP". 
If it returns something, your battery supports this function.<br><br>

If supported by the battery, a new sysctl is created: dev.battery.X.Warning_Level<br>
Replace the X with your battery index (0, 1, ...). <br>

You can set the warning level ("trip point") with this sysctl (values between 0-100 are allowed).<br>
If the battery reaches that percentage, devd will be notified.<br>
The value 0 disables the warning.<br>

Next add an entry in /etc/devd.conf:<br>
notify 10 {<br>
	match "system" "ACPI";<br>
	match "subsystem" "CMBAT";<br>
	action "/home/myuser/myscript.sh $notify";<br>
};<br>

Replace myuser with your local user. Replace myscript.sh with a script of your choice.<br>

Personal note: If you have any questions, please write me. Then I will look at this again.<br>
 Thanks. :-)

 __Installation guide for beginners:__<br>
 
Step 1:
Try the command: "acpidump -dt |grep _BTP". 
If it returns something, your battery supports this function.<br><br>

Step 2:
Donwload the Freebsd source code. <br>
Replace the file from this repo with the file /usr/src/sys/dev/acpica/acpi_cmbat.c<br>

Step 3:
Build and install the new kernel.

Step 4:
Add an entry in /etc/devd.conf:<br>
notify 10 {<br>
	match "system" "ACPI";<br>
	match "subsystem" "CMBAT";<br>
	action "/home/myuser/myscript.sh $notify";<br>
};<br>

Step 5:
Replace mysuser and myscript with an actual user and an actual script.<br>

Step 6:
Set the sysctl dev.battery.0.Warning_Level to your desired warning level. If it works, give me feedback.<br>
