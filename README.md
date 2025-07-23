🌅 The Dawn Bot
===============

A fully automated bot with modular architecture for registration, verification, farming, task completion, and more.

* * * * *

🚀 Installation Guide (Python Source)
-------------------------------------

* * * * *

🪟 Windows Setup
----------------

### 1\. Install Python (version 3.10+)

-   Download from: <https://www.python.org/downloads/>

-   During installation, make sure to check:

    -   ✅ "Add Python to PATH"

* * * * *

### 2\. Clone the Repository

```
git clone https://github.com/xxin-han/Dawn-New.git
cd Dawn-New
unzip Dawn-New.zip
cd Dawn-New
```

* * * * *

### 3\. Create and Activate a Virtual Environment

```
python -m venv venv
source venv\bin\activate
```

* * * * *

### 4\. Install Dependencies

```
pip install --upgrade pip
pip install -r requirements.txt
```

* * * * *

### 5\. 🔧 Configure the Bot (IMPORTANT)

Ensure the `config` folder is placed inside the project directory.

This step is crucial to let the bot function properly. Here's a breakdown of the modules, required input files, and available settings.


### 6\. Run the Bot

Copy

```
python run.py
```

You're done! 🎉

* * * * * * * * * * * * * * *

## 🐧 Ubuntu/Linux Setup

### 1\. Install Python & Git

Open terminal and run:

Copy

```
sudo apt update
sudo apt install python3 python3-venv python3-pip git -y
```

* * * * *

### 2\. Clone the Repository

Copy

```
git clone https://github.com/xxin-han/Dawn-New.git
unzip my_project.zip
cd Dawn-New
```

* * * * *

### 3\. Create and Activate a Virtual Environment

Copy

```
python3 -m venv venv
source venv/bin/activate
```

* * * * *

### 4\. Install Dependencies

Copy

```
pip install --upgrade pip
pip install -r requirements.txt
```

* * * * *

### 5\. 🔧 Configure the Bot (IMPORTANT)

Ensure the `config` folder is placed inside the project directory.

This step is crucial to let the bot function properly. Here's a breakdown of the modules, required input files, and available settings.
* * * * *

### 6\. Run with Screen (Recommended)

Install `screen` if you don't have it:

Copy

```
sudo apt install screen -y
```

Create and enter a screen session:

Copy

```
screen -S dawn-bot-session
```

Run the bot:

Copy

```
python run.py
```

To detach (keep it running):

`Ctrl+A`, then press `D`

* * * * *


📌 Screen Commands Reference

Copy

```
# List all screen sessions
screen -ls

# Reattach to a session
screen -r dawn-bot-session

# Delete a session
screen -X -S dawn-bot-session quit
```



# User Guide - Getting Started
============================
Configuration File Formats

------------------------------

### proxies.txt

1.  Navigate to the file `proxies.txt` (config > data)

2.  Add proxies in one of the following formats:

Copy

```
http://user:pass@ip:port
http://ip:port:user:pass
http://ip:port@user:pass
socks5://user:pass@ip:port
socks5://ip:port:user:pass
socks5://ip:port@user:pass
```

### register_accounts.txt

1.  Navigate to the file register_accounts`.txt` (config > data)

2.  Add accounts in the following format:

Copy

```
email:email_password
```

### login_accounts.txt

1.  Navigate to the file `login_accounts.txt` (config > data)

2.  Add accounts in the following format:

Copy

```
email:dawn_password
```

### verify_accounts.txt

1.  Navigate to the file `verify_accounts.txt` (config > data)

2.  Add accounts in the following format:

Copy

```
email:email_password
```

### export_stats_accounts.txt

1.  Navigate to the file `export_stats_accounts.txt` (config > data)

2.  Add accounts in the following format:

Copy

```
email
```

### complete_tasks_accounts.txt

1.  Navigate to the file `complete_tasks_accounts.txt` (config > data)

2.  Add accounts in the following format:

Copy

```
email
```

### farm_accounts.txt

1.  Navigate to the file `farm_accounts.txt` (config > data)

2.  Add accounts in the following format:

Copy

```
email
```

### referral_code.txt

1.  Navigate to the file `referrals_codes.txt` (config > data)

2.  Add codes in the following format (only code):

Copy

```
hegbhf
```

## Settings.yaml Configuration

-----------------------------------------------------------------------------------------------------------------------------------------------------------

* * * * *

### Application Settings

Copy

```
application_settings:
  threads: 10                     # Number of concurrent threads
  keepalive_interval: 300        # Interval for keep-alive pings (in seconds)
  database_url: "sqlite://database/database.sqlite3"  # Database connection URI
  skip_logged_accounts: false    # Skip accounts that are already logged in
  shuffle_accounts: true         # Randomize account processing order
```

-   threads: Controls the number of concurrent operations. Higher values increase performance but require more resources.

-   keepalive_interval: Time interval in seconds between keep-alive signals to maintain session.

-   database_url: Database connection string. SQLite used by default. For PostgreSQL, use format: `postgres://user:pass@host/db_name`

-   skip_logged_accounts: When enabled, already authenticated accounts will be skipped.

-   shuffle_accounts: Processes accounts in random order to reduce pattern detection.

* * * * *

### Redirect Settings

Copy

```
redirect_settings:
  enabled: false                 # Enable or disable email redirection
  email: ""                      # Email address for login code retrieval
  password: ""                   # Password for email account
  imap_server: ""                # IMAP server to connect to
  use_proxy: false               # Use proxy for IMAP connections
```

-   enabled: Master switch for enabling redirection through IMAP.

-   imap_server: Server used to read mail (e.g., `imap.gmx.net`).

-   use_proxy: If true, IMAP connection will use a proxy.

-   Format for mails in files login_accounts.txt and register_accounts.txt: email:any password (any password, because the software will search for the letter in the main mail that you specified)

* * * * *

### Captcha Solving Services

Copy

```
captcha_settings:
  captcha_service: "anticaptcha"     # Options: 2captcha, anticaptcha
  max_captcha_solving_time: 120      # Maximum time to wait for a solution (in seconds)

  two_captcha_api_key: ""            # API key for 2captcha
  anti_captcha_api_key: ""           # API key for Anticaptcha
```

-   captcha_service: Choose your preferred captcha solving provider.

-   max_captcha_solving_time: Max wait time for a captcha response.

* * * * *

### Attempts and Delay Settings

Copy

```
attempts_and_delay_settings:
  delay_before_start:
    min: 0                           # Minimum delay before starting operations (seconds)
    max: 3                           # Maximum delay before starting operations (seconds)

  error_delay: 5                     # Delay after an error occurs (seconds)

  max_register_attempts: 10         # Max registration attempts
  max_login_attempts: 5             # Max login attempts
  max_stats_attempts: 3             # Max stats fetching attempts
  max_tasks_attempts: 3             # Max task completion attempts
  max_attempts_to_receive_app_id: 3 # Max attempts to fetch app_id
  max_attempts_to_verify_email: 10  # Max attempts to verify email
  max_attempts_to_send_keepalive: 3 # Max attempts to send keep-alive pings
```

-   Use these settings to control retry limits and delays for operations.

-   Random delays help distribute system load.

* * * * *

### IMAP Configuration

Copy

```
imap_settings:
  use_proxy_for_imap: true

  use_single_imap:
    enable: false
    imap_server: "imap.gmail.com"

  servers:
    gmail.com: imap.gmail.com
    yahoo.com: imap.mail.yahoo.com
    icloud.com: imap.mail.me.com
    mail.ru: imap.mail.ru
    gmx.com: imap.gmx.com
    gmx.net: imap.gmx.net
    gmx.de: imap.gmx.net
    onet.pl: imap.poczta.onet.pl
    onet.com.pl: imap.poczta.onet.pl
    op.pl: imap.poczta.onet.pl
    onet.eu: imap.poczta.onet.pl
    gazeta.pl: imap.gazeta.pl
    jammer.dev: imap.smtp.dev
    retroletter.ru: mail.twc.com
    firemail.eu: imap.firemail.de
```

-   use_proxy_for_imap: Controls proxy usage during email fetching.

-   use_single_imap: Allows overriding IMAP server globally.

-   servers: Domain-to-server mappings for automatic IMAP resolution.

