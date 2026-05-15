# RMU Combat Storyboard

![Latest Version](https://img.shields.io/badge/Version-1.0.0-blue)
![Foundry Version](https://img.shields.io/badge/Foundry_VTT-v14_%7C_v14-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)
![RTL Support](https://img.shields.io/badge/RTL-Supported-green)
![Download Count](https://img.shields.io/github/downloads/Filroden/rmu-combat-storyboard/rmu-combat-storyboard.zip)
![Download Count](https://img.shields.io/github/downloads/Filroden/rmu-combat-storyboard/latest/rmu-combat-storyboard.zip)
![Last Commit](https://img.shields.io/github/last-commit/Filroden/rmu-combat-storyboard)
![Issues](https://img.shields.io/github/issues/Filroden/rmu-combat-storyboard)

## Welcome to RMU Combat Storyboard

This module is designed exclusively for the Rolemaster Unified (RMU) system.

Rolemaster combats are famously detailed, featuring highly tactical phases, specific hit locations, and devastating critical injuries. The **RMU Combat Storyboard** is a Game Master utility that captures this rich mechanical data and translates it into a highly compressed, token-efficient prompt designed for external Large Language Models (LLMs like ChatGPT, Gemini, or Claude).

The result? Raw combat logs are transformed into cinematic, multi-page comic book scripts and detailed image generation prompts, allowing you to immortalise your group's most epic battles.

## Key features

- **Silent Hook Ingestion:** Automatically captures attacks, spells, resistance rolls, and area-of-effect impacts during combat, saving them securely to a Journal Entry.
- **The Storyboard Wizard:** A dedicated UI accessible from the Combat Tracker to curate your combat highlight reel.
- **Cast & Roster Management:** Define the visual descriptions of your combatants and the environment to ensure AI consistency.
- **Hero Moments:** Flag specific attacks or critical hits to guarantee they become the focal point of the generated story.
- **Plain Text Export:** For GMs who just want a clean, human-readable summary of the battle without using AI, the module provides a one-click downloadable text log.

## How to use (inside FoundryVTT)

1. **Run Your Combat:** Play out your RMU encounter normally. When the combat ends, you (GMs only) will be prompted to save the raw event log to a Journal Entry.
2. **Open the Wizard:** Click the Storyboard Wizard icon (the crossed swords) located at the top of the Combat Tracker sidebar.
3. **Configuration Tab:** * Select your saved combat log from the dropdown menu.
    - Choose your **Prompt Style** (Script Only, or Script & Image Prompts).
    - Choose an **Art Style** (e.g., Dark & Gritty, 1980s Retro, Manga).
    - Set a **Target Page Count** to dictate the length of the final comic.
    - Provide a brief **Campaign Context** (e.g., "A rainy night in a muddy forest clearing") to ground the AI.
4. **Cast & Roster Tab:** Review the combatants. Replace their mechanical names with physical descriptions (e.g., "A small halfling wearing soft leather"). This prevents the image generator from hallucinating character names as floating text.
5. **Highlight Reel Tab:** Review the timeline of the battle. Check the **Hero Moment** box next to the most important actions to guarantee they receive a massive spotlight panel in the final script. You can also download a human-readable text file of the log from here.
6. **Export Prompt Tab:** The module compiles your entire curated battle into a dense, token-optimised code block. Click **Copy to Clipboard**.

## How to use (external LLM workflow)

Because modern AI models perform best when their attention isn't split, this module separates the roles of the **Writer** (generating the story) and the **Artist** (generating the images).

### Step 1: Generate the script

Paste the copied prompt from the "Export Prompt" tab into your preferred text-based LLM (such as ChatGPT, Gemini, or Claude).

The LLM will process the dense mechanical notation, follow the layout rules included by the module, and output a formatted comic book script for you to read, complete with camera angles and sound effects.

### Step 2: Generate the art (optional)

If you selected the **Script & Image Prompts** option, your LLM will also output self-contained code blocks labeled `Image Prompt: Page X`.

Copy these blocks *one by one* and paste them back into an image-generation model (like ChatGPT Plus/DALL-E 3, Gemini Pro, or Midjourney). The prompt has already been sanitised of game mechanics and character names, forcing the image model to strictly draw the visual action in your chosen art style.

## Important note on localisation

The RMU Combat Storyboard is fully translation-ready and supports RTL layouts. However, when working with the exported AI prompt, you will notice a specific architectural design: **Mixed-Language Prompting.**

- **The System Instructions are always in English.** To ensure the LLM strictly follows complex logical constraints (like preventing meta-commentary, parsing system mechanics, and formatting image prompts), the core rules are hardcoded in English, which matches the bulk of the LLM's training data.
- **The Output will be in your language.** The prompt automatically detects your Foundry VTT language setting and issues an instruction to the AI. The LLM will read your localised Campaign Context, process the English rules, and output the final cinematic comic script in your chosen language.
