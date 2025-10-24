# 🚀 Gluetun-Arr-Stack: The Complete Self-Hosted Media Server

This Docker Compose file provides a robust, pre-configured solution for a complete **Arr Stack** media server setup, specifically designed for users facing **geo-restrictions** (like blocked metadata sources such as TMDB) or in regions with **strict torrent monitoring**.

---

## 📦 Stack Components

This `docker-compose.yml` file orchestrates the following services to create a fully automated media management system:

| Service | Function |
| :--- | :--- |
| **Prowlarr** | Indexer manager for searching across all your torrent trackers. |
| **Sonarr** | Automated TV series downloading and management. |
| **Radarr** | Automated movie downloading and management. |
| **qBittorrent** | The primary torrent download client. |
| **Gluetun** | A **VPN client** (WireGuard/OpenVPN) that routes all specified container traffic securely. |
| **Flaresolverr** | A proxy service to bypass Cloudflare and similar CAPTCHA protection on certain indexers. |
| **Jellyfin** | The media server used for viewing and streaming your downloaded movies and TV series. |
| **Jellyseerr** | A request management system to easily search and request media without directly accessing Radarr/Sonarr. |

---

## ✨ Key Features & Problem Solved

This specific configuration is tailored to overcome common hurdles encountered by users in countries with restricted internet access and those concerned about piracy monitoring.

1.  **Comprehensive Geo-Restriction Bypass:**
    * The **Arr Stack** (Sonarr/Radarr/Prowlarr) routes its search traffic through **Gluetun** (VPN), ensuring blocked indexers are accessible.
    * **Jellyfin** also routes its **metadata lookups** through the VPN, guaranteeing access to accurate and complete metadata (e.g., from TMDB), which is often blocked or unreliable in certain countries (such as India).

2.  **Privacy and Security:**
    * All download traffic (via **qBittorrent**) and media management traffic is securely routed through the **Gluetun VPN container**, significantly mitigating risks associated with torrent patrolling and ensuring download privacy.

3.  **Jellyseerr/Gluetun Interoperability Workaround:**
    * A critical configuration is included to ensure **Jellyseerr** can communicate with the **Jellyfin** container, even though Jellyfin is connected to the isolated VPN network managed by Gluetun. This ensures a seamless user experience for media requests.

4.  **Quick and Easy Deployment:**
    * Most of the compose file is written so a person starting out his or her journey just has to replace the **placeholders** and configure the containers to achieve a self-hosted multimedia server.

---

## ⚠️ Prerequisites & Setup Instructions

### 1. VPN Requirement

**NOTE:** **A commercial VPN service is required** to use this setup. The Gluetun container needs valid credentials for a VPN provider.

### 2. Gluetun Configuration

* Refer to the official **Gluetun Wiki** (linked in the `docker-compose.yml` file) to find the specific environment variables and settings required for your chosen VPN provider.
* **Cyber Law Advisory:** It is highly recommended to **choose a VPN server located in a country with liberal cyber laws** to maximize your privacy and safety.

### 3. Post-Installation Configuration Guidance

If you are not experienced with Docker, configuring the required volume paths and necessary container connections after initial deployment can be complex.

For a detailed, step-by-step guide on:
* Which **folder paths** to insert into the placeholders.
* The necessary **post-installation configurations** within each container (e.g., setting up indexers in Prowlarr, connecting Sonarr/Radarr, and setting up remote path mappings).

Please follow this helpful resource:
**[YouTube Guide](https://www.youtube.com/watch?v=3k_MwE0Z3CE)**
