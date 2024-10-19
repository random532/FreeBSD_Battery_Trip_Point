# FreeBSD Battery Warnings
<br>
THIS NEEDS AN UPDATE FOR CURRENT FREEBSD VERSION!

Affected file:<br>
sys/dev/acpica/acpi_cmbat.c<br>

<br>
Short description:<br>
Get notified if your battery reaches a user-defined percentage.<br>
<br>
Long description:<br>
There is no need to run a daemon that regularly checks the battery level.<br>
Just tell the battery controller your desired warning level via the optional acpi method _BTP. <br>

Your battery supports this if the command "acpidump -dt |grep _BTP" returns something (an acpi method).<br><br>

Currently the FreeBSD cmbat driver only supports mandatory methods (bif, bix, ..), but no optional ones.<br>

If supported by the battery, a new sysctl is created, dev.battery.0.Warning_Level<br>
You can set the warning level with this sysctl (values between 0-100).
Once the battery reaches that level, devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>

A /etc/devd.conf entry might look like this:<br>
notify 10 {<br>
	match "system" "ACPI";<br>
	match "subsystem" "CMBAT";<br>
	action "/home/myuser/myscript.sh $notify";<br>
};<br>

<br>
Personal note: Please write me if I need to look at this again.<br>
For example, if it no longer compiles. Thanks. :-)
