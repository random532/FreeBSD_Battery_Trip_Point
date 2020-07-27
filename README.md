# patch_cmbat.c
Battery warning level for FreeBSD control method batteries (_BTP) :-)
<br>
The patch applies to the file (/usr/src/)sys/dev/acpica/acpi_cmbat.c<br>
If supported by the battery, a new sysctls will be created:<br> 
dev.Battery.X.Warning_Level<br>
<br>

devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>
