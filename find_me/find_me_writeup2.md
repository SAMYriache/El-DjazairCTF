# CTF Write-Up: Find Me Challenge

## Challenge Information
- **Challenge Name:** Find Me
- **Author:** COn4n
- **Category:** OSINT/Investigation
- **Difficulty:** Medium
- **Date:** May 25, 2025

## Challenge Description
The "Find Me" challenge presents a simple but intriguing riddle with three clues:
- **Bot**
- **Memes** 
- **Tropical**

The goal is to find what these three clues are pointing to and capture the flag.

## Initial Analysis

Looking at the three clues, I needed to find something that connects all three concepts:
- **Bot** - Likely a Discord bot or similar automated service
- **Memes** - Related to meme content or sharing
- **Tropical** - Could be a theme, name, or visual element

## Solution Process

### Step 1: Research Phase
I started by searching for combinations of these terms to see what would come up. A Google search for "Bot Memes Tropical" yielded interesting results.

![Google Search Results](image1.png)

The search revealed two potential candidates:
- **Tropical Bot** - A multifunctional Discord bot
- **Memes bot** - A bot specifically for memes

### Step 2: Investigating the Memes Bot
The "Memes bot" seemed like the most promising lead since it directly matched two of our clues. I found it on Discord bot directories.

![Discord Bot Directory](image2.png)

Perfect match! The "Memes bot" had:
- ✅ **Bot** - It's a Discord bot
- ✅ **Memes** - Specifically designed for memes (videos + pictures)  
- ✅ **Tropical** - Uses a pineapple emoji (🍍) as its icon/theme

Key details discovered:
- Name: "Memes bot 🍍"
- Description: "First Arabic bot for memes (videos + pictures) This bot will make your server active !!"
- Rating: 4.1 stars
- The pineapple clearly represents the "tropical" element

### Step 3: Finding the Creator
I investigated who created this bot to understand more about it.

![Creator Profile](image3.png)

Found the creator's Discord profile:
- Username: **COn4n** (y.abderrahmane)
- Developer with skills in JavaScript, TypeScript, Python
- Joined Discord 7 years ago

![Bot Creators](image4.png)

The bot has multiple creators:
- b2raa
- tt4k  
- y.abderrahmane

### Step 4: Locating the Discord Server
Every Discord bot typically has a support server. I found references to the bot's community.

![Bot Information](image5.png)

Key information discovered:
- Server count: 187 servers
- Official website: bot.arb-memes.com
- Has a Discord Support Server

### Step 5: Accessing the Support Server
I joined the "Memes Support" Discord server and explored the channels.

![Discord Server Solution](image6.png)

**SUCCESS!** In the #soon channel, I found the welcome message containing the flag:

```
Bienvenue dans #soon ! 
C'est le début du salon #soon. El-DjazairCTF{Oh_YOU_f0und_MY_mEMes_b0t}
```

## Flag
```
El-DjazairCTF{Oh_YOU_f0und_MY_mEMes_b0t}
```

## Solution Summary

The three clues led me to identify the **"Memes bot"** Discord bot:
1. **Bot** → Discord bot platform
2. **Memes** → Bot's primary function (sharing memes)
3. **Tropical** → Pineapple theme/icon (🍍)

The flag was hidden in the welcome message of the bot's support Discord server in the #soon channel.

## Tools Used
- Google Search Engine
- Discord Bot Directories (top.gg)
- Discord Application
- Basic OSINT investigation techniques

## Key Insights
- Visual elements (like emojis) can represent abstract clues
- Bot creators often have dedicated Discord servers for support
- Welcome messages in Discord channels can contain hidden information
- Sometimes the most direct interpretation of clues is correct

## Lessons Learned
- Always investigate community spaces related to your target
- Pay attention to branding elements (icons, themes) as they may relate to clues
- Discord servers often contain valuable information in channel descriptions and welcome messages
- OSINT challenges often require following a logical chain of discoveries

---

*This write-up documents my solution process for the "Find Me" OSINT challenge. The key was connecting the three clues to identify the specific Discord bot and then locating its community server where the flag was hidden.*