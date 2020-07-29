# FreeBSD Battery Warnings
<br>

Affected file:<br>
sys/dev/acpica/acpi_cmbat.c in 12.1 base<br>
<br>
Description:<br>
If supported by the battery (_BTP), a new sysctl is created:<br> 
dev.battery.0.Warning_Level<br>
devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>
