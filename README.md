# 🪟  Windows Server 2022 on Proxmox – Installation and Configuration

Complete setup of a Windows Server 2022 virtual machine within my home lab using Proxmox. The VM was configured with VirtIO drivers, RDP access, and the QEMU Guest Agent enabled for smooth remote management.
---

## 📚 Lingua / Language

- 🇬🇧 [English version](#english-version)
- 🇮🇹 [Versione italiana](#versione-italiana)


---

## 🇬🇧 English Version

### 1. Goal

Deploy a Windows Server 2022 VM with:
- VirtIO drivers (disk and network)
- Remote Desktop access
- Post-installation snapshot
- Guest agent active

---

### 2. Requirements

- Windows Server 2022 ISO
- VirtIO drivers ISO (`virtio-win.iso`)
- Proxmox Web UI access

---

### 3. VM Creation on Proxmox

Configuration used:
- Name: `win-srv`
- ISO: Windows Server 2022
- OS Type: Microsoft Windows (11/2022)
- BIOS: OVMF (UEFI)
- Machine: q35
- Hard Disk: 60 GB – VirtIO Block
- CPU: 2 cores
- RAM: 4096 MB
- Network: vmbr0 – VirtIO (paravirtualized)

Added second CD-ROM with VirtIO ISO (`virtio-win.iso`).

---

### 4. Windows Server Installation

- Chose **Standard (Desktop Experience)** version
- No disk detected → loaded driver from:
  `viostor > w11 > amd64`
- Disk appeared and installation proceeded normally

---

### 5. Additional Drivers Installed

From VirtIO ISO:
- **NetKVM** → network driver (`NetKVM > w11 > amd64 > netkvm.inf`)
- **Balloon** → RAM management (`Balloon > w11 > amd64 > balloon.inf`)
- **QEMU Guest Agent** already active (verified via `services.msc`)

---

### 6. Remote Desktop Enabled

- `This PC → Properties → Remote Desktop → Enabled`
- Added user to allow access
- Tested via `mstsc` from another PC → clipboard sharing works

---

### 7. Final Snapshot

Snapshot created:
- **Name:** `win-clean-install`
- **Description:** Windows Server installed, updated, configured with drivers and RDP

---

### 8. About

Created by **Sebastiano Daniele Condorelli**  
LinkedIn: [www.linkedin.com/in/sebastianodanielecondorelli](https://www.linkedin.com/in/sebastianodanielecondorelli)  
2025

--

## 🇮🇹 Versione italiana

### 1. Obiettivo

Creare una VM Windows Server 2022 con:
- Driver VirtIO (disco e rete)
- Accesso Desktop Remoto
- Snapshot post-installazione
- Guest agent attivo

---

### 2. Requisiti

- ISO di Windows Server 2022
- ISO dei driver VirtIO (`virtio-win.iso`)
- Proxmox con accesso web

---

### 3. Creazione VM in Proxmox

Impostazioni usate:
- Nome: `win-srv`
- ISO: Windows Server 2022
- OS Type: Microsoft Windows (11/2022)
- BIOS: OVMF (UEFI)
- Machine: q35
- Hard Disk: 60 GB – VirtIO Block
- CPU: 2 core
- RAM: 4096 MB
- Rete: vmbr0 – VirtIO (paravirtualized)

Aggiunto un secondo CD-ROM con l’ISO dei driver VirtIO (`virtio-win.iso`).

---

### 4. Installazione Windows Server

- Selezionata versione **Standard (Desktop Experience)**
- Nessun disco rilevato → Caricato driver da:
  `viostor > w11 > amd64`
- Dopo il caricamento, disco rilevato correttamente

---

### 5. Driver aggiuntivi installati

Dalla ISO VirtIO:
- **NetKVM** → driver rete (`NetKVM > w11 > amd64 > netkvm.inf`)
- **Balloon** → gestione RAM dinamica (`Balloon > w11 > amd64 > balloon.inf`)
- **QEMU Guest Agent** già presente → confermato attivo (`services.msc`)

---

### 6. Abilitazione Desktop Remoto

- `This PC → Proprietà → Remote Desktop → Attivato`
- Aggiunto utente per l’accesso
- Testato con `mstsc` da un altro PC → copia/incolla funzionante

---

### 7. Snapshot finale

Creato snapshot chiamato:
- **Nome:** `win-clean-install`
- **Descrizione:** Windows Server installato, aggiornato e configurato con driver e accesso remoto

---

### 8. Info personali

Creato da **Sebastiano Daniele Condorelli**  
LinkedIn: [www.linkedin.com/in/sebastianodanielecondorelli](https://www.linkedin.com/in/sebastianodanielecondorelli)  
2025


