# Personal Operational Security Setup

## Overview
When I started learning about cybersecurity, I realized that I was already thinking like a defender by being security concious in my personal life. This documents my personal setup and transition away from Google ecosystem (Gmail, Chrome, and Google search) to privacy-focused alternatives (Proton, Tor, and DuckDuckGo).


## Email Strategy

### Domain
I have a main Proton email that I basically never use directly or give out.

- **Registration:** through Porkbun

- **Email Provider:** Proton Mail (end-to-end encrypted)

- **Authentication:** SPF, DKIM, DMARC all configured



### Email Aliasing (SimpleLogin)
Instead of giving services my real email, every website/company gets a separate and unique alias. All emails received by an alias are forwarded to my Proton email.

**How it works:** Amazon gets shopping.abc123@8alias.com and Netflix gets streaming.def456@slmails.com

**Why I do this:**

- **Breach containment:** If(when) a service gets hacked, attackers only get that one alias. I disable it, create a new one, update my account. My other accounts stay safe.

- **Spam tracking:** If an alias starts getting spam, I know exactly which company leaked/sold my data and can disable that specific alias without touching anything else.

- **Replying to emails:** SimpleLogin utilizes "reverse alias" meaning I can reply to emails and it shows the alias as the sender instead of my email.

## Password Management
Every account has a unique, randomly generated password (20+ charaters). I don't know any of my passwords except my master pasword.

**Tool:** Proton Pass (zero-knowledge encryption)

**Why zero-knowledge matters:**
- Even if Proton's servers got hacked, attackers would only get encrypted data which is useless without my master password.
- Proton itself cannot even see my passwords.

## Multi-Factor Authentication

I use 2FA on every account that has it.

**My hierarchy:**
1. Hardware security keys (YubiKey) - for critical stuff like email and password manager
2. TOTP authenticator apps - for most accounts
3. SMS - only when there's no other choice

## Network Security

**VPN:** Proton VPN running 24/7 on all devices for traffic encryption and protection on public WiFi

## What I'm learning from this
- How authentication actually works in real life beyond theory
- What a breach response looks like in practice
- Threat modeling - what/who all I am actually protecting myself from
- Value of layered security - if one thing fails, I have backups

## What I Still Want to Add Later
- Another layer of security via home network
- Better backup strategy for important files
