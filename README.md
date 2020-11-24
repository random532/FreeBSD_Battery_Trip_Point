# FreeBSD Battery Warnings
<br>

In file:<br>
sys/dev/acpica/acpi_cmbat.c<br>
<br>
Description:<br>
If supported by the battery (_BTP), a new sysctl is created, dev.battery.0.Warning_Level<br>
You can set the warning level (in percent) with this sysctl.
Once the battery reaches that level, devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>

Your battery supports this if the command "acpidump -dt |grep _BTP" returns something (an acpi method).
