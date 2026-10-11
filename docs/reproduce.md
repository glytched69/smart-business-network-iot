# Open and Inspect the Simulation

## Requirements

Use Cisco Packet Tracer **9.0.0**, the version recommended by the original coursework. Obtain the simulator from Cisco; it is not bundled. No Python, npm, Docker or real network equipment is required.

1. Download or clone the repository.
2. Open `Topologie-projet-8.pkt` through Packet Tracer's **File > Open**.
3. Work on a copy so device experiments do not replace the supplied topology.
4. Select Realtime mode and allow routing and switching to converge. Use Fast Forward Time if necessary.

## Review Path

| Check | Where and how | What to inspect |
| --- | --- | --- |
| VLAN segmentation | Switch CLI: `show vlan brief` | VLANs 10 (Employees), 15 (SOC/IT), 20 (IoT), 30 (Visitors), 99 (Management). |
| Trunking | Switch CLI: `show interfaces trunk` | Relevant VLANs carried on configured trunk links. |
| Routing | Router CLI: `show ip ospf neighbor`, `show ip route` | OSPF neighbours and routes for the configured subnets. |
| ACLs | Router CLI: `show access-lists`, `show ip interface` | Rule order and the interfaces/directions where rules apply. |
| Connectivity | End device Desktop > Command Prompt: `ipconfig`, `ping <destination>` | Use addresses from the topology. Compare permitted and denied paths against actual ACLs, not VLAN names alone. |
| HSRP | R1/R2 CLI: `show standby brief` | Active/standby states and virtual gateway. |
| Failover | Save a baseline copy, disable an active router interface or power off the active router | Inspect the standby router becoming active and connectivity returning after convergence. Restore the device afterwards. |
| RFID and sensors | Device Config/Programming and IoT dashboard | Existing event rules and actuator states for access, motion and fire scenarios. |

Some CLI commands require `enable`. Use only the laboratory credentials already associated with the supplied project; do not substitute credentials from a real network. If a command is unavailable on a simulated device, inspect its Config tab instead.

The private addressing is part of the simulation; it does not refer to your home network. IoT actions are simulated device events, not real alarms or physical controls.

## File Integrity

`Topologie-projet-8.pkt`: **599,496 bytes**.

SHA-256:

```text
345473545814e01f01f8f1f9f668721b8c5ffdfb9e057ef25c6ae49cab65ac6c
```

Windows PowerShell:

```powershell
Get-FileHash .\Topologie-projet-8.pkt -Algorithm SHA256
```

The hash checks download integrity, not network correctness. Packet Tracer 9.0.0 was found installed on the review machine, but the topology was not rerun during this publication review. The [report figures](project-overview.md) are historical evidence; use the checks above to reproduce them.

## Troubleshooting

- File does not open: check version and download integrity; do not rename the extension.
- First ping fails: allow ARP/routing convergence, then retry before diagnosing an ACL.
- No connectivity after failover: inspect the virtual default gateway, HSRP states, trunk VLANs and routes.
- Sensor scenario does not trigger: inspect device registration and programmed event conditions in the saved topology.

See the [project overview](project-overview.md) for the original design and credited screenshots.
