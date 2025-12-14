# Bake Game - Simple Website

This is a very basic HTML, CSS, and JavaScript website for the **Bake Games** company.
It contains static pages with simple content and no backend or advanced features.

## Purpose

- Display important information about the company
- Act as a personal portfolio for Bake Games and ME hehe

## Project Overview

- **Server OS:** Linux
- **Web Server:** Nginx (handles reverse proxy, load balancing, HTTP caching, HTTPS termination)
- **Domain:** Registered with Registro.br under account `FNSFR6` (associated with personal Gmail)
- **Cloudflare:** Used for tunneling, proxying, and IPv6 → IPv4 handling
- **HTTP → HTTPS:** All HTTP requests are redirected to HTTPS
- **SSL Certificates:** Stored in `/etc/ssl/private/` (root access required)
- **Server Type:** IPv6-only server, proxied via Cloudflare to support IPv4 access
- **Workflow** If you want to work on this website, you can just deploy a local server using live server or similar tools. When finished, just ssh into the raspberry and pull from origin. I did not see a reason to divide this into prod and making CIs yet. DO NOT FORGET TO CLEAR YOUR CACHE

## Accessing the Raspberry Pi Locally

1. Ensure you are connected to the Raspberry Pi’s **Wi-Fi**
2. Use the server username: `sirmadeira`
3. Run:

   ```bash
   arp -a
   ```

   to see local IPs. Connect to the IP that matches the Raspberry Pi.
   _Note: Static IPv4 setup can be tricky depending on your router._

4. Connect via SSH:

   ```bash
   ssh sirmadeira@[RaspberryPiIP]
   ```

   In this case the easiest to way identify is just enter your router: http://192.168.0.1/2.0/gui/login, and he will show everyone connected to it!

---

## Managing Nginx Configuration

1. SSH into the Raspberry Pi
2. Edit the main Nginx config for your site:

   ```bash
   /etc/nginx/sites-available/bakegames.com.br
   ```

   _This is the only symlinked file in `sites-enabled`—it is the active site._

3. Test configuration after any change:

   ```bash
   sudo nginx -t
   ```

4. If something goes wrong, check the error log:

   ```bash
   /var/log/nginx/error.log
   ```

## No IPV6 address being assigned

1. Take a loot at this forum https://forums.raspberrypi.com/viewtopic.php?t=311451, and done
2. In my case it something decided it was a good idea to block my IPV6
