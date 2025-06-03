# 🛡️ Deploy Your Own Proxy with Outline on DigitalOcean (Dedicated IP)

This guide walks you through setting up a personal encrypted proxy using [Outline](https://getoutline.org/) on a VPS, giving you full control and a dedicated IP address for your browsing and network activity.

---

## ✨ Why Use This?

- ✅ Dedicated static IP address
- ✅ Encrypted Shadowsocks proxy
- ✅ Easy to manage via Outline Manager
- ✅ Great for privacy, bypassing geo-blocks, and secure access

---

## 🧰 Requirements

- A [DigitalOcean](https://digitalocean.com) account (or any VPS provider like Vultr, Linode, Hetzner)
- A VPS running Ubuntu (tested on 22.04+)
- SSH access to the server
- [Outline Manager](https://getoutline.org/) installed on your local computer

---

## 🚀 Step-by-Step Setup

### 1. Create a VPS

- Create a Droplet (VPS) on DigitalOcean with:
  - **1 vCPU / 1 GB RAM**
  - Ubuntu 22.04 or newer
  - **Choose a region** that matches the IP location you want (e.g., US)
  - Use **SSH authentication** or set a root password

### 2. Connect via SSH

If you used an SSH key:

```bash
ssh root@<your_droplet_ip>
```

### 3. Install Outline Server (Manually)

If `get.outline.org` fails, run the **official GitHub script**:

```bash
curl -sS https://raw.githubusercontent.com/Jigsaw-Code/outline-server/master/src/server_manager/install_scripts/install_server.sh | bash
```

At the end, it will give you a JSON block like:

```json
{
  "apiUrl": "https://<your_ip>:<port>/<access-token>",
  "certSha256": "..."
}
```

### 4. Open Ports on Your VPS

Make sure the following ports are open on your firewall (DigitalOcean usually allows all by default):

| Port   | Protocol     | Purpose               |
|--------|--------------|------------------------|
| 1273   | TCP          | Outline management     |
| 25132  | TCP and UDP  | Proxy traffic          |

---

## 🖥️ Connect in Outline Manager

1. Open Outline Manager
2. Click **"Install Outline Anywhere"**
3. Click **"Already installed Outline"**
4. Paste the JSON block from step 3

Now you can manage access keys (proxies), monitor traffic, etc.

---

## 📱 Connect via Outline Client

Install the Outline client on your devices:

- [macOS](https://itunes.apple.com/app/outline-app/id1356178125)
- [iOS](https://apps.apple.com/app/outline-app/id1356177741)
- [Android](https://play.google.com/store/apps/details?id=org.outline.android.client)

Paste or scan the access key to start routing your traffic.

---

## 🔒 Notes

- Your IP will remain static **unless you destroy the droplet**
- Optional: use a [Reserved IP](https://docs.digitalocean.com/products/networking/reserved-ips/) for added stability
- You can share access with others by generating multiple keys

---

## ✅ Done!

You now have a secure, fast, and private proxy running on your own server with a dedicated IP address 🎉
