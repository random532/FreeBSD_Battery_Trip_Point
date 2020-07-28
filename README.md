# Battery Warnings
<br>
<br>
In: (/usr/src/)sys/dev/acpica/acpi_cmbat.c<br>

Description:
If supported by the battery (_BTP), a new sysctl is created:<br> 
dev.battery.0.Warning_Level<br>
<br>
devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>
