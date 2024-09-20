---
title: OpenBSD 7.4 -current arm64
published: true
---

# [](#header-1)Instalando OpenBSD 7.4 -current (arm64) on hetzner cloud.

[Hetzner](https://www.hetzner.com/cloud) introdujo servidores arm64 basados en
Ampere Ultra, los cuales son compatibles con el port de
[OpenBSD](http://www.openbsd.org) arm64.

### [](#header-3) Notas sobre la instalacion.

1. Abre una cuenta en [Hetzner](https://www.hetzner.com/login)
2. Selecciona una instancia, en mi caso CAX11
3. Instala Ubuntu o Debian
4. Inicia sesion como root
5. Descarga el instalador de OpenBSD 7.4 -current
6. Escribe la imagen del archivo en la unidad de almacenamiento.

```shell
wget https://cdn.openbsd.org/pub/OpenBSD/snapshots/arm64/miniroot74.img
dd if=miniroot74.img of=/dev/sda bs=4M
```

La instancia CAX11 provee 2 vCPU, 4GB RAM y 40GB SSD.

comparto el dmesg.

```
OpenBSD 7.4-current (GENERIC.MP) #33: Mon Dec 25 01:14:23 MST 2023
    deraadt@arm64.openbsd.org:/usr/src/sys/arch/arm64/compile/GENERIC.MP
real mem  = 4185792512 (3991MB)
avail mem = 3972055040 (3788MB)
random: good seed from bootblocks
mainbus0 at root: ACPI
psci0 at mainbus0: PSCI 1.1, SMCCC 1.1
efi0 at mainbus0: UEFI 2.7
efi0: EDK II rev 0x10000
smbios0 at efi0: SMBIOS 3.0.0
smbios0: vendor Hetzner version "20171111" date 11/11/2017
smbios0: Hetzner vServer
cpu0 at mainbus0 mpidr 0: ARM Neoverse N1 r3p1
cpu0: 64KB 64b/line 4-way L1 PIPT I-cache, 64KB 64b/line 4-way L1 D-cache
cpu0: 1024KB 64b/line 8-way L2 cache
cpu0: DP,RDM,Atomic,CRC32,SHA2,SHA1,AES+PMULL,LRCPC,DPB,ASID16,PAN+ATS1E1,LO,HPDS,VH,HAFDBS,CSV3,CSV2,SBSS+MSR
cpu1 at mainbus0 mpidr 1: ARM Neoverse N1 r3p1
cpu1: 64KB 64b/line 4-way L1 PIPT I-cache, 64KB 64b/line 4-way L1 D-cache
cpu1: 1024KB 64b/line 8-way L2 cache
cpu1: DP,RDM,Atomic,CRC32,SHA2,SHA1,AES+PMULL,LRCPC,DPB,ASID16,PAN+ATS1E1,LO,HPDS,VH,HAFDBS,CSV3,CSV2,SBSS+MSR
apm0 at mainbus0
agintc0 at mainbus0 shift 4:4 nirq 288 nredist 2 ipi: 0, 1, 2: "interrupt-controller"
agintcmsi0 at agintc0
agtimer0 at mainbus0: 25000 kHz
acpi0 at mainbus0: ACPI 5.1
acpi0: sleep states
acpi0: tables DSDT FACP APIC PPTT GTDT MCFG SPCR DBG2 IORT BGRT
acpi0: wakeup devices
acpimcfg0 at acpi0
acpimcfg0: addr 0x4010000000, bus 0-255
acpiiort0 at acpi0
"ACPI0007" at acpi0 not configured
"ACPI0007" at acpi0 not configured
pluart0 at acpi0 COM0 addr 0x9000000/0x1000 irq 33
pluart0: console
```
