# 🚀 Render Keep-Alive Workflow 😴➡️☕️

This repository helps keep your Render apps awake! ☀️ It uses a GitHub Actions workflow to send periodic HTTP requests, preventing those pesky sleeps. 💤

## ✨ Purpose

Render's free tier (and sometimes paid tiers too!) lets apps doze off 😴 after inactivity. This workflow sends `curl` requests 📬 to your app endpoints, keeping them responsive and ready! ⚡️

**⚠️ Important!** Using GitHub Actions minutes for this? ⏱️ Consider Render's ping URLs instead! They're the recommended way. 😉

## 🛠️ Workflow Details

Check out the `wakeup.yml` file in `.github/workflows/`! 📂

### ⏰ Schedule

Runs every 14 minutes! 🔄

### 🚀 Usage

1.  **Clone it!** ⬇️

    ```bash
    git clone https://github.com/GunanshuJoshi/wakey-wakey.git
    ```

2.  **Edit `wakeup.yml`!** 📝 in `wakey-wakey/.github/workflows/`:

    * Update those `curl` commands with your Render app URLs! 🔗

    ```yaml
    name: Keep Render Apps Alive 
    on:
      schedule:
        - cron: '*/14 * * * *'
    jobs:
      keep_alive:
        runs-on: ubuntu-latest
        steps:
          - name: Wake up Render Apps ☕️
            run: |
              #!/bin/bash
              curl --fail-with-body https://your-app1.onrender.com &
              curl --fail-with-body https://your-app2.onrender.com &
              curl --fail-with-body https://your-app3.onrender.com &
    ```

3.  **Push it!** ⬆️ to your own repo.

4.  **Watch the magic!** ✨ Go to the "Actions" tab to see it run. 🏃‍♂️💨

### 🤔 Important Things to Know

* **Minute Muncher!** ⏱️ This workflow uses GitHub Actions minutes! Running it every 14 minutes adds up! 💸
* **Render Ping FTW!** 🏆 Render's ping URLs are the best way to keep your apps awake! 🥇
* **Error Alert!** 🚨 `curl --fail-with-body` makes sure you know if anything goes wrong! 💥
