# patch_cmbat.c
This adds battery warning levels to FreeBSD control method batteries - highly experimental :-)

The patch applies to the file (/usr/src/)sys/dev/acpica/acpi_cmbat.c<br>
Up to three new sysctls:<br> 
dev.cmbat.0.Any<br>
dev.cmbat.0.Low<br>
dev.cmbat.0.CriticallyLow<br>
<br>
It probably crashes if you have more than one battery.

Catch the warnings via devd "CMBAT" notifications.<br>
