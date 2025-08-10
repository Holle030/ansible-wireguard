# Ansible WireGuard VPN Setup

Dieses Projekt installiert und konfiguriert WireGuard zwischen einem Raspberry Pi und einem öffentlichen Server (z. B. holle.port4949.de) über ein sicheres Peer-to-Peer-VPN.

## Sicherheit
- Die Schlüssel liegen in `secrets/` und sind in `.gitignore` ausgeschlossen.
- Niemals Private Keys oder sensible Konfigurationsdateien ins Repository committen!
- Die Konfiguration wird aus Jinja2-Templates mit lokalen Schlüsseln zur Laufzeit erzeugt.

## Projektstruktur (Ausschnitt)
```
ansible-wireguard/
├── inventory/
│   └── hosts.ini
├── playbook.yml
├── roles/
│   └── wireguard/
│       ├── tasks/
│       ├── templates/
│       └── defaults/
├── secrets/     # ← NICHT versionieren!
├── .gitignore
└── README.md
```

## Ausführen

```bash
ansible-playbook -i inventory/hosts.ini playbook.yml
```

## Voraussetzungen

- SSH-Zugriff auf Client und Server
- Installiertes `ansible`, `wireguard` und gültige Schlüsselpaare in `secrets/`
- Python 3 auf den Zielsystemen

## ✅ Status

Getestet unter:
- Debian 12 (Server)
- Raspberry Pi OS Bookworm (Client)
