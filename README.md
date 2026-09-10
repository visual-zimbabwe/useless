# useless

A simple command-line tool that brings random facts and the fact of the day right into your computer terminal with visual text animations.

## What is useless?

useless is a lightweight Linux terminal application. It connects to the free Useless Facts API over the internet, gets a trivia fact, formats it neatly so words are not cut in half, and animates the text onto your screen using a tool called ttfx.

## Requirements

Before installing, make sure you have these standard command-line tools on your system:

- bash (the default command shell on Linux)
- curl (used to download information from the web)
- jq (a small tool used to read data from APIs)
- ttfx (a tool that animates text inside the terminal)
- wl-copy or xclip (optional, used if you want to copy facts to your clipboard)

On Arch Linux and Omarchy, you can ensure they are installed by running:

```bash
sudo pacman -S curl jq
```

## How to Install

1. Download or clone this repository to your computer:

```bash
git clone https://github.com/visual-zimbabwe/useless.git ~/apps/useless
```

2. Make the script executable:

```bash
chmod +x ~/apps/useless/bin/useless
```

3. Create a link so you can run the command from any folder:

```bash
mkdir -p ~/.local/bin
ln -sf ~/apps/useless/bin/useless ~/.local/bin/useless
```

Now you can type `useless` anywhere in your terminal.

## How to Use

### 1. Show the Daily Fact
Get today's official fact of the day:

```bash
useless
```

### 2. Get a Random Fact
Fetch a fresh random fact whenever you want:

```bash
useless random
```

### 3. Change the Animation Effect
You can change how the text appears on your screen with the `-e` option:

```bash
# Matrix green digital rain
useless random -e matrix

# Classic typewriter effect
useless random -e print

# Neon beams effect
useless random -e beams

# Pick a surprise animation every time
useless random -e -R
```

### 4. Copy to Clipboard
Add the `-c` flag to copy the fact straight to your clipboard so you can paste it to a friend:

```bash
useless -c
```

### 5. Raw Text Output
If you want to use the text in another script without any visual animation, use `--raw`:

```bash
useless --raw
```

## How It Works

1. When you run the command, it sends a request to `https://uselessfacts.jsph.pl`.
2. It cleans up the text and wraps the lines to fit your terminal window width.
3. It passes the clean text to `ttfx`, which renders the selected animation.
