# Defensive Controls

The project demonstrates how physical access can expose an offline attack surface on Windows systems when appropriate endpoint and boot protections are not in place.

The following controls can reduce the impact of unauthorized physical access.

---

## 1. Full-Disk Encryption

### BitLocker

Enable **BitLocker** or another appropriate full-disk encryption solution on Windows endpoints.

Full-disk encryption is one of the most important controls demonstrated by this project because it protects data at rest when an attacker attempts to access the storage device through an alternative operating environment.

Without effective encryption, accessing the physical storage device can potentially expose locally stored information independently of the normal Windows authentication screen.

### Security objective

```text
Physical access
      │
      ▼
Alternative boot environment
      │
      ▼
Encrypted storage
      │
      ▼
Data remains protected
```

---

## 2. UEFI / BIOS Security

Firmware configuration should be protected against unauthorized changes.

Where supported, organizations should consider:

- Setting an administrator password for firmware configuration
    
- Reviewing available boot-device settings
    
- Preventing unauthorized changes to the boot configuration
    
- Restricting access to firmware settings
    

The exact configuration depends on the device manufacturer and organizational requirements.

---

## 3. Restrict External Boot

External boot devices can provide an alternative operating environment.

Where operationally appropriate, organizations can restrict booting from:

- USB devices
    
- External storage
    
- Other unauthorized boot media
    

This should be implemented carefully because recovery and IT-support workflows may require controlled external boot capabilities.

---

## 4. Secure Boot

**UEFI Secure Boot** can provide an additional layer of protection by helping ensure that trusted boot components are used during system startup.

Secure Boot should be enabled where supported and compatible with the organization's operating requirements.

It should be considered as part of a broader endpoint-security strategy rather than as a replacement for full-disk encryption.

---

## 5. Protect Recovery Keys

Full-disk encryption is only useful if its recovery mechanism is managed securely.

Recovery keys should:

- Be stored separately from the endpoint
    
- Be protected from unauthorized access
    
- Be available to authorized administrators when required
    
- Be included in the organization's recovery procedures
    

Recovery processes should be tested before an incident occurs.

---

## 6. Physical Security

Physical security is an important component of endpoint security.

Organizations should consider:

- Securing unattended computers
    
- Controlling physical access to sensitive systems
    
- Using appropriate device locks
    
- Maintaining asset-management procedures
    
- Establishing procedures for lost or stolen devices
    

A lost or stolen device should be treated as a potential security incident.

---

## 7. Windows Authentication Is Not the Only Security Boundary

A Windows password protects access through the normal Windows authentication mechanism.

However, the project demonstrates why authentication should not be considered the only layer of endpoint protection.

A simplified model is:

```text
                Endpoint
                   │
        ┌──────────┴──────────┐
        │                     │
        ▼                     ▼
 Windows Authentication   Physical Access
        │                     │
        ▼                     ▼
    OS Access             Boot Security
                              │
                              ▼
                       Storage Encryption
```

Multiple layers should work together.

---

## 8. Defense-in-Depth

A hardened endpoint should combine several controls rather than depend on a single protection mechanism.

### Example layered model

```text
┌─────────────────────────────────┐
│        Physical Security        │
├─────────────────────────────────┤
│          UEFI / BIOS            │
├─────────────────────────────────┤
│          Secure Boot            │
├─────────────────────────────────┤
│       Full-Disk Encryption      │
├─────────────────────────────────┤
│      Windows Authentication     │
├─────────────────────────────────┤
│      Endpoint Security Controls │
└─────────────────────────────────┘
```

Each layer addresses a different part of the attack surface.

---

## 9. Backups

Important data should be backed up independently of the endpoint.

A robust backup strategy helps ensure that:

- Data can be recovered after device failure
    
- Recovery does not depend solely on the local disk
    
- Security incidents do not result in permanent data loss
    

Backups should also be tested periodically.

---

## 10. Lost or Stolen Devices

Organizations should have a defined response process for lost or stolen Windows endpoints.

Recommended actions may include:

1. Report the device as missing.
    
2. Determine whether the device contains sensitive information.
    
3. Verify whether full-disk encryption was enabled.
    
4. Protect or rotate relevant credentials where necessary.
    
5. Review available device-management and security telemetry.
    
6. Follow the organization's incident-response procedures.
    

---

# Recommended Security Baseline

For systems containing sensitive information, a layered configuration can include:

|Control|Security Purpose|
|---|---|
|**BitLocker / Full-Disk Encryption**|Protect data at rest|
|**UEFI / BIOS Password**|Protect firmware configuration|
|**Secure Boot**|Protect the boot chain|
|**External Boot Restrictions**|Reduce unauthorized alternate boot|
|**Windows Authentication**|Protect normal OS access|
|**Physical Security**|Reduce unauthorized physical access|
|**Secure Recovery-Key Storage**|Protect encryption recovery mechanisms|
|**Regular Backups**|Enable reliable data recovery|

---

# Key Takeaway

The main defensive lesson from this project is:

> **Windows authentication should be combined with storage encryption and boot/firmware security to provide meaningful protection against physical attacks.**

A device can have a strong Windows password while still exposing significant risk if an unauthorized person can physically access the storage and boot an alternative environment.

Full-disk encryption, appropriate UEFI/BIOS configuration, Secure Boot, physical security, and reliable backups provide complementary layers of protection.

---

## Scope

These recommendations are intended for authorized endpoint-security assessment, security awareness, and defensive hardening.

The controls should be evaluated according to the organization's hardware, operating-system configuration, recovery requirements, and security policies.
