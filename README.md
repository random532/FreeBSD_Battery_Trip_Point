# patch_cmbat.c
Battery warning level for FreeBSD control method batteries (_BTP)- highly experimental :-)


The patch applies to the file (/usr/src/)sys/dev/acpica/acpi_cmbat.c<br>
Up to three new sysctls:<br> 
dev.cmbat.0.BatteryWarningAny  (read-write)<br>
dev.cmbat.0.BatteryWarningLow  (read-only)<br>
dev.cmbat.0.BatteryWarningCritical  (read-only)<br>
<br>
It probably crashes if you have more than one battery.

Catch the warnings via devd "CMBAT" notifications.<br>
