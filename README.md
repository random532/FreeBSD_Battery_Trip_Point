# FreeBSD Battery Warnings
<br>

In file:<br>
sys/dev/acpica/acpi_cmbat.c  (13 Current)<br>
<br>
Description:<br>
If supported by the battery (_BTP), a new sysctl is created, dev.battery.0.Warning_Level<br>
devd will be notified via system "ACPI" subsystem "CMBAT" events.<br>
