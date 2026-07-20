If your Mac is running out of storage, there are several ways to quickly identify the largest files.

## Method 1: About This Mac (Fastest)

1. Click ** > About This Mac**
2. Go to **Storage**
3. Click **Storage Settings...**
4. Review:

   * Applications
   * Documents
   * Developer
   * Trash
   * iCloud Drive

Under **Documents**, you'll often find a **Large Files** section listing the biggest files.

---

## Method 2: Finder Search (My Favorite)

1. Open **Finder**
2. Press **⌘ + F**
3. Change:

   * Search: **This Mac**
   * Kind → **Other...**
   * Select **File Size**
4. Set:

```
File Size
is greater than
500 MB
```

Sort by **Size**.

You'll immediately see all files larger than 500 MB.

---

## Method 3: Terminal (Very Powerful)

Open Terminal.

### Largest files on your Mac

```bash
sudo find / -type f -size +500M 2>/dev/null
```

or

```bash
find ~ -type f -size +500M
```

Only searches your Home folder.

---

### Top 20 largest files

```bash
find ~ -type f -exec du -h {} + | sort -hr | head -20
```

---

### Largest folders

```bash
du -sh ~/* | sort -hr
```

Example:

```
120G Movies
65G Downloads
42G Library
18G Documents
```

---

## Method 4: DaisyDisk (Highly Recommended)

This is one of the best storage visualization apps for macOS.

It shows:

* Huge files
* Hidden folders
* Xcode data
* Old backups
* Duplicate data

You can free tens of GB within minutes.

---

## Method 5: Check Xcode (Developers)

Since you're building **Dharma Connect**, Xcode is often the biggest storage consumer.

### Derived Data

```bash
rm -rf ~/Library/Developer/Xcode/DerivedData/*
```

Usually frees **10–50 GB**.

---

### Device Support

```bash
~/Library/Developer/Xcode/iOS DeviceSupport
```

Delete versions you no longer need.

---

### Archives

```
~/Library/Developer/Xcode/Archives
```

Old archives can consume **20–100 GB**.

---

### Simulators

Check:

```
~/Library/Developer/CoreSimulator
```

or run:

```bash
xcrun simctl delete unavailable
```

---

## Method 6: Downloads Folder

Often overlooked.

Sort Downloads by **Size**.

You may find:

* Old ZIPs
* DMGs
* IPSW firmware
* Videos
* Large PDFs

---

## Method 7: Docker (if installed)

```bash
docker system df
```

Clean up with:

```bash
docker system prune -a
```

---

## Method 8: Homebrew Cleanup

```bash
brew cleanup
```

---

## Method 9: Check What's Using Space

Run:

```bash
sudo du -hxd1 / | sort -hr
```

Or for your home directory:

```bash
du -hxd1 ~ | sort -hr
```

This gives a folder-by-folder breakdown.

---

### For your setup (Xcode + Firebase + AI development), I'd check these in order:

1. ✅ `~/Library/Developer/Xcode/DerivedData`
2. ✅ `~/Library/Developer/Xcode/Archives`
3. ✅ `~/Library/Developer/CoreSimulator`
4. ✅ `~/Downloads`
5. ✅ `~/Movies`
6. ✅ `~/Library/Application Support/MobileSync/Backup` (old iPhone/iPad backups)
7. ✅ `~/Library/Caches`

It's common for Xcode developers to recover **50–100 GB** just by cleaning Derived Data, old archives, and unused simulators.
