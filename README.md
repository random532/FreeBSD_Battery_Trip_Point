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

Try the command: "acpidump -dt |grep _BTP" 
If it returns something, your battery supports this function.<br><br>

If supported by the battery, a new sysctl is created: dev.battery.X.Warning_Level<br>
Replace the X with your battery index (0, 1, ...). <br>

You can set the warning level ("trip point") with this sysctl (values between 0-100 are allowed).<br>
If the battery reaches that percentage, devd will be notified.<br>

Add an entry in /etc/devd.conf:<br>
notify 10 {<br>
	match "system" "ACPI";<br>
	match "subsystem" "CMBAT";<br>
	action "/home/myuser/myscript.sh $notify";<br>
};<br>

Replace myuser with your local user. Replace myscript.sh with a script of your choice.<br>

Personal note: If you have any questions, please write me. I will look at this again.<br>
 Thanks. :-)
