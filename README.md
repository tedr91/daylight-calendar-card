[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/hacs/integration)
[![GitHub release](https://img.shields.io/github/release/superdingo101/daylight-calendar-card.svg)](https://github.com/superdingo101/daylight-calendar-card/releases)
[![GitHub stars](https://img.shields.io/github/stars/superdingo101/daylight-calendar-card.svg)](https://github.com/superdingo101/daylight-calendar-card/stargazers)
![Github All Releases](https://img.shields.io/github/downloads/superdingo101/daylight-calendar-card/total.svg)
[![GitHub issues](https://img.shields.io/github/issues/superdingo101/daylight-calendar-card.svg)](https://github.com/superdingo101/daylight-calendar-card/issues)
[![License](https://img.shields.io/github/license/superdingo101/daylight-calendar-card.svg)](LICENSE)
<a href="https://github.com/sponsors/superdingo101"><img src="https://img.shields.io/badge/Sponsor-GitHub%20Sponsors-pink?style=for-the-badge&logo=github" alt="GitHub Sponsors" style="height: 20px !important;" ></a>
<a href="https://buymeacoffee.com/superdingo101"><img src="https://img.shields.io/badge/Donate-Buy%20me%20a%20beer-yellow?style=for-the-badge&logo=buy-me-a-coffee" alt="Buy Me a Coffee" style="height: 20px !important;" ></a>

# Daylight Calendar Card for Home Assistant

> [!IMPORTANT]
> **Project renamed:** `skylight-calendar-card` is now `daylight-calendar-card`.
>
> Existing dashboard YAML using `type: custom:skylight-calendar-card` continues to work, for now. New naming and configuration examples will transition gradually.

A bright, family-friendly calendar card for Home Assistant dashboards.

Designed for clarity at a glance, with flexible views and deep customization.

---

## ✨ Features

* 📅 **Compact Week View** – Clean, glanceable layout for daily planning
* 🗓️ **Schedule View** – Detailed list-style agenda
* 👨‍👩‍👧‍👦 **Multi-calendar support** – Combine multiple calendars into one view
* 📝 **Full event management** – Create, edit, and manage events (integration dependent)
* ✨ **Rich event descriptions** – Display Markdown, basic HTML, and safe inline markup in event details
* 🌤️ **Weather forecast display** – Built-in weather insights alongside your schedule
* 🎨 **Highly customizable** – Layout, styling, visibility, and behavior options
* ⚡ **Fast & responsive** – Optimized for wall tablets and dashboards

---

## 📸 Preview

### Week View

![Week View](https://github.com/user-attachments/assets/8a772a66-3ce7-4f78-aeab-d0abb50ac27b)

### Schedule View

![Schedule View](https://github.com/user-attachments/assets/eb3852b6-0f7f-477c-9e6d-3c5741f6cb77)

### Agenda View

<p align="center">
  <img src="https://github.com/user-attachments/assets/6610248e-716a-420c-972b-e427d4a65582" width="300" alt="Agenda View"/>
</p>

---

## 🔧 Requirements

* Home Assistant
* One or more calendar entities (e.g. `calendar.family`, `calendar.work`)

---

## 🚀 Installation

### Recommended: Install via HACS

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=superdingo101&repository=daylight-calendar-card&category=frontend)

OR

1. Open **HACS → Frontend**
2. Click **+ Explore & Download Repositories**
3. Search for **Daylight Calendar Card**
4. Install and refresh your dashboard

👉 If you don’t have HACS yet, follow: [https://hacs.xyz/docs/use/](https://hacs.xyz/docs/use/)

---

### Manual Installation

<details>

<summary>Without HACS</summary>

1. Download:
   [https://raw.githubusercontent.com/superdingo101/daylight-calendar-card/refs/heads/main/skylight-calendar-card.js](https://raw.githubusercontent.com/superdingo101/daylight-calendar-card/refs/heads/main/skylight-calendar-card.js)
2. Place in:
   `<config>/www/skylight-calendar-card.js`
3. Add resource:

   ```
   /local/skylight-calendar-card.js?v=1
   ```
4. Set type to **JavaScript Module**
5. Refresh your browser

💡 After updates, bump the version (`?v=2`) to avoid caching issues.

</details>

---

## ⚡ Quick Start

```yaml
type: custom:daylight-calendar-card
title: Family Calendar
entities:
  - calendar.family
```

---


## 📚 Documentation

Daylight Calendar Card includes a visual configurator for most common options.

Some advanced features are supported by the card but must be configured in YAML.

If you do not see an option in the visual editor, open the card in YAML mode. YAML-only features include:

- `event_styles` — conditionally style individual events and add matched event icons (`icon`, `icon_color`, `icon_size`, `icon_position`)
- `day_styles` — conditionally style days
- `virtual_calendars` — group multiple calendars into a single virtual calendar
- Advanced UIX/Card Mod styling

Example `event_styles` icon rule:

```yaml
event_styles:
  - match:
      title: practice
    style:
      background_color: orange
      icon: mdi:basketball
      icon_color: white
      icon_size: 16px
      icon_position: before_title # or corner
```

Full documentation is available in the wiki:

* Installation
* Configuration
* Views & Navigation
* Event Management
* Troubleshooting
* UIX / Card Mod compatibility
* Development

<p align="center">
  <a href="https://github.com/superdingo101/daylight-calendar-card/wiki">
    <img src="https://img.shields.io/badge/Docs-Read%20the%20Wiki-blue?logo=github&style=for-the-badge" />
  </a>
</p>

---

## 💡 Tips

* Use multiple calendars for a shared family dashboard
* Pair with wall-mounted tablets for a Daylight-style experience
* Combine with UIX/Card Mod for advanced styling
* In Home Assistant Sections view, put `grid_options.rows` directly on the `custom:daylight-calendar-card` / `custom:skylight-calendar-card` card for reliable row sizing. Stacked layouts such as `vertical-stack` may also need the stack or wrapper card to participate in height distribution before children can fill the allocated rows.

---

## 🛠 Troubleshooting


### I don't see the last changes
1. Check that your Daylight Calendar Card version is the latest in HACS.
2. Check that the latest Daylight card is actually loaded. Starting in v4.4.0, the downloaded and running version is displayed in the **About / Diagnostics** section of the visual editor.
3. Clear your cache :
   * check Settings → Dashboards → Resources
   * remove any versions of `/hacsfiles/daylight-calendar-card/skylight-calendar-card.js`
   * remove any versions of `/hacsfiles/skylight-calendar-card/skylight-calendar-card.js`
   * uninstall Daylight from HACS
   * reinstall Daylight from HACS
   * Refresh your browser
   * Clear app/browser cache

Still stuck? Open an issue

---

## 💬 Community & Support

If you need help, have ideas, or want to contribute, use the options below:

<p align="center">
  <a href="https://github.com/superdingo101/daylight-calendar-card/issues">
    <img src="https://img.shields.io/badge/GitHub-Issues-green?logo=github&style=for-the-badge" />
  </a>
  <a href="https://github.com/superdingo101/daylight-calendar-card/discussions">
    <img src="https://img.shields.io/badge/GitHub-Discussions-lightgrey?logo=github&style=for-the-badge" />
  </a>
  <a href="https://community.home-assistant.io/t/skylight-calendar-card-a-family-friendly-schedule-card/981221/17">
    <img src="https://img.shields.io/badge/Home%20Assistant-Community%20Forum-blue?logo=home-assistant&style=for-the-badge" />
  </a>
</p>

---

## 💪 Support this project

If you'd like to support development, GitHub Sponsors is the preferred option ❤️

<p align="center">
  <a href="https://github.com/sponsors/superdingo101">
    <img src="https://img.shields.io/badge/Sponsor-GitHub%20Sponsors-pink?style=for-the-badge&logo=github" />
  </a>
  <a href="https://buymeacoffee.com/superdingo101">
    <img src="https://img.shields.io/badge/Donate-Buy%20me%20a%20beer-yellow?style=for-the-badge&logo=buy-me-a-coffee" />
  </a>
</p>

---

## ❤️ Acknowledgements

Thanks to the Home Assistant community for feedback, ideas, and contributions.

Your support helps shape the future of this project!
