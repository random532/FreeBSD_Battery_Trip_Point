# patch_acpi_cmbat.c
<br>
The patch applies to the file (/usr/src/)sys/dev/acpica/acpi_cmbat.c<br>
If supported by the battery (_BTP), a new sysctls will be created:<br> 
dev.battery.0.Warning_Level<br>
<br>

devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>
