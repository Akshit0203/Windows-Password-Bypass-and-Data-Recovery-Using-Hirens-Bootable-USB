# Methodology

This document describes the methodology followed during the Windows password bypass and data-recovery exercise using Hiren's BootCD PE.

> **Scope:** The procedure was performed for authorized cybersecurity testing, endpoint-security research, and digital-forensics education.

---

## Phase 1 — Preparing the Bootable USB

The first step was to obtain the Hiren's BootCD PE ISO and prepare a bootable USB drive using Rufus.

### Requirements

- Hiren's BootCD PE ISO
    
- Rufus
    
- USB flash drive
    
- Authorized Windows test system
    

The Hiren's BootCD PE ISO was selected in Rufus and written to the USB drive.

### Evidence

![Hiren's BootCD PE and Rufus](../images/hiren's%20boot%20iso%20and%20rufus.png)

![Rufus](../images/rufus.png)

![Hiren Bootable USB Files](../images/Hiren%20bootable%20usb%20files.jpg)

---

## Phase 2 — Booting the Test System

The prepared USB drive was connected to the authorized Windows test system.

The system was restarted and the firmware/boot-device selection interface was accessed.

The exact procedure and boot key can vary depending on the manufacturer and model of the computer.

The Hiren's BootCD PE USB was then selected as the boot device.

### Evidence

![Windows Boot Menu](../images/windows%20boot%20menu.png)

---

## Phase 3 — Accessing the Windows System Volume

After Hiren's BootCD PE loaded, the Windows system volume was accessible from the PE environment.

The Windows installation and its user directories could be examined independently of the normal Windows login interface.

A typical user-data location is:

```text
C:\Users\
```

The required data was then copied to external storage as part of the authorized recovery exercise.

### Evidence

![Data Recovery](../images/data%20recovery.JPG)

![Data Recovery File Location](../images/data%20recovery%20file%20location.JPG)

---

## Phase 4 — Offline Windows Account Recovery

The project evaluated two utilities available within the Hiren's BootCD PE environment for offline Windows account recovery:

- NT Password Edit
    
- Windows Login Unlocker
    

### NT Password Edit

NT Password Edit was opened from the Hiren's BootCD PE environment.

The Windows installation was selected, followed by the relevant user account.

The available account-management options were then examined.

### Evidence

![NT Password Edit](../images/NT%20Password%20edit.JPG)

![NT Password Edit](../images/nt%20passoword%20edit.JPG)

---

### Windows Login Unlocker

Windows Login Unlocker was also evaluated as an alternative offline account-recovery utility.

The relevant Windows account was selected and the available recovery/unlock functionality was examined.

### Evidence

![Windows Login Unlocker](../images/Windows%20login%20unlocker.JPG)

![Windows Login Unlocker](../images/windows%20login%20unlocker%202.JPG)

---

## Phase 5 — Deleted File Recovery

The project also included a deleted-file recovery exercise using Recuva Wizard.

The recovery workflow involved selecting the type of data to search for and specifying the location where the deleted files were expected to exist.

Possible file categories included:

- Pictures
    
- Documents
    
- Videos
    
- Emails
    
- Other supported file types
    

### Evidence

![Recuva Wizard](../images/recuva%20wizard.JPG)

![Recuva File Type Selection](../images/recuva%20wizard%20file%20type.JPG)

---

## Phase 6 — Data Backup

Data identified during the recovery process could be copied to external storage.

The purpose of this phase was to demonstrate the amount of information that may become accessible when an attacker has physical access to an insufficiently protected endpoint.

### Evidence

![Data Recovery](../images/data%20recovery.JPG)

![Data Recovery File Location](../images/data%20recovery%20file%20location.JPG)

---

## Phase 7 — Security Analysis

The exercise demonstrated that the security boundary provided by Windows authentication can be significantly affected when an attacker has physical access to the machine and can boot an alternative environment.

The project therefore examined the importance of:

- Full-disk encryption
    
- BitLocker
    
- BIOS/UEFI security
    
- Boot-device restrictions
    
- Secure Boot
    
- Physical security
    
- Secure recovery-key management
    

The main security observation was that an unencrypted storage device can expose locally stored data to offline access even when the normal Windows login interface is protected by a password.

---

## Methodology Summary

```text
Hiren's BootCD PE ISO
          │
          ▼
      Rufus USB
          │
          ▼
   Boot Test System
          │
          ▼
    Hiren's BootCD PE
          │
     ┌────┴─────┐
     │          │
     ▼          ▼
 Account      Data
 Recovery     Access
     │          │
     ▼          ▼
NT Password   User Data
Edit /        Backup
Login Unlocker
     │
     └────┬─────┘
          ▼
    Recuva Wizard
          │
          ▼
 Deleted File Recovery
          │
          ▼
   External Storage
```

---

## Conclusion

The methodology provided practical exposure to offline Windows security, physical attack surfaces, account recovery, and data recovery.

The exercise also demonstrated why endpoint security should extend beyond the operating-system login screen. Full-disk encryption and appropriate firmware/boot protections are important controls for reducing the impact of unauthorized physical access.

All activities documented in this repository were intended for an authorized test environment.